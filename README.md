> NOTE  
> This guide explains how to host the resume using GitLab Pages, following the workflow described in *Modern Technical Writing*. The university GitLab instance used for this assignment does not provide CI runners, so the live version of the site was deployed using GitHub Pages instead. The documentation itself still demonstrates the GitLab Pages workflow.
# Hosting a Resume Website Using MkDocs and GitLab Pages
## Purpose
This document explains how to create and publish a resume using modern technical documentation tools. The goal is to show how a resume written in Markdown can be converted into a website using a static site generator and hosted online with the help of a forge and a version control platform.

This guide is written with Marvin McLaren in mind. He is the finance manager at Foomatic. Like Marvin, you should have basic familiarity with Markdown, and I will assume you also have little to no experience with Git, static site generators, or software development tools. We will be performing simple command line operations, so if you know the basics in that regard you are good to go.

By following this guide, you will learn how to turn a Markdown document into a fully hosted website. The guide also demonstrates key ideas from Andrew Etter's *Modern Technical Writing*, which promotes using simple tools and automated systems for writing and publishing documentation.

Etter argues that modern technical documentation should rely on four main components:
* Lightweight markup languages
* Distributed version control systems
* Static site generators
* Forges for hosting code and documentation

This project uses Markdown, Git, MkDocs, and GitLab Pages to demonstrate these principles in practice.

This guide demonstrates the workflow recommended in *Modern Technical Writing*: writing documentation in a lightweight markup language, managing it with version control, generating a static website, and publishing it through a forge.
## Prerequisites
Before starting, you will need the following tools installed on your computer.
### Required Software
* Python - required to run MkDocs
* Git - Used for version control
* MkDocs - static site generator used to create the website
* A web browser
* A GitLab account

### Basic Knowledge
You should already know:
* basic Markdown formatting
* how to open a terminal
* how to run simple commands

Andrew Etter emphasizes using tools that are easy to learn and widely available. Markdown and Git are commonly used in modern documentation workflows because they are simple, flexible, and compatible with many platforms.

## Instructions
The following steps explain how Marvin or anyone else who meets the prerequisites can create and host a resume website.

### Step 1: Create a new MkDocs project
1. First, install MkDocs by running the following command in your terminal:
```shell
pip install mkdocs
```
2. After you have successfully installed MkDocs, you want to create a project and go into the directory
```
mkdocs new my-project
cd my-project
```
> [!NOTE]
> 'my-project' is a placeholder for the project name and you should choose what it should be.
3. To host your MkDocs server locally, make sure you are in the project directory and run
```shell
mkdocs serve
```
After this runs successfully, you will be able to find your static website running locally in your browser at the address:
```
http://127.0.0.1:8000
```
### Step 2: Write the resume in Markdown
Next, open the file located at:
```
docs/index.md
```
This file will become the homepage of the website. You may replace the existing content with your resume information.

Example:
```md
# Steve Kakina Mateso

## Education
University of Manitoba  
Bachelor of Science in Computer Science

## Skills
- C++
- Python
- Git
```
Markdown is an example of a lightweight markup language. According to Etter, lightweight markup languages are ideal for documentation because they keep files readable while still allowing them to be converted into structured websites. Unlike complex document formats, Markdown files can be easily stored in version control systems.
### Step 3: Configure the Website
MkDocs uses a configuration file called:
```
mkdocs.yml
```
This file defines the website's title and navigation.
Example configuration:
```yml
site_name: Steve Kakina Mateso Resume

nav:
  - Resume: index.md
```
This configuration tells MkDocs to display the Markdown file as the main page.

Static site generators like MkDocs automate the process of turning documentation into websites. Etter recommends static site generators because they make publishing documentation faster and more consistent.

### Step 4: Initialize version control with Git
Create a Git repository to track changes to the project.

Run the following commands:
```shell
git init
git add .
git commit -m "Initial commit"
```
Git is a distributed version control system, which Etter recommends for managing documentation projects. Version control systems allow authors to track revisions, collaborate with others, and maintain a history of changes. We will use Git to publish the resume website online.

### Step 5: Create a repository on GitLab
Create a repository on GitLab and connect it to your project so the site can be hosted online. GitLab will be used to host the resume website.

After creating the repository on GitLab, run:
```shell
git remote add origin https://gitlab.com/username/resume-site.git
git push -u origin main
```
GitLab is an example of a **forge**, a platform that hosts code repositories and allows collaboration between developers and writers.

Andrew Etter recommends publishing documentation on forges because they provide version control hosting, collaboration tools, and automated publishing systems.

### Step 6: Configure GitLab Pages
GitLab Pages allow static websites to be hosted automatically from a git repository.

To enable this, create a file named:
```
.gitlab-ci.yml
```
Example configuration:
```yml
image: python:3.11

before_script:
  - pip install mkdocs

pages:
  script:
    - mkdocs build
    - mv site public
  artifacts:
    paths:
      - public
  only:
    - main
```
This file tells GitLab to automatically build the MkDocs site and publish it as a website.

Automation like this is another principle discussed in *Modern Technical Writing*. Automated systems reduce manual effort and ensure documentation is always published consistently.

### Step 7: Access the published website
Once the pipeline finishes running, Marvin's website will be available online. The URL usually looks like this:
```
https://username.gitlab.io/repository-name
```
The Markdown resume is now publicly available as a static website.

This workflow demonstrates the complete process recommended by Etter:
1. Writing the documentation in Markdown
2. Storing it in version control
3. Generating a static website
4. Hosting it on a forge
## Further Resources
- [Markdown Guide](https://www.markdownguide.org/basic-syntax/)
- [MkDocs documentation](https://www.mkdocs.org/)
- [Git Documentation](https://git-scm.com/)
- [GitLab Pages Documentation](https://docs.gitlab.com/user/project/pages/)
- [Modern Technical Writing by Andrew Etter](https://www.amazon.ca/Modern-Technical-Writing-Introduction-Documentation-ebook/dp/B01A2QL9SS/ref=sr_1_1?crid=2CIPEV7ORVVEO&dib=eyJ2IjoiMSJ9.93wLcMZhK_JKMGGvtIoUDQ51_XAoWwFCav1fXnkU-NPudkq0g9Rmo9msTPsPQOzRzyUigHCQi8UYO7i5RO1esYp3UU6WMz_eUcm1r2u_fBMhX8ngvbfx0HG64AZdwH0GrDy9c5nE049aFX6S23bVRypcTsGZLSel5RJQhhtiEcYyYNggWL8kU4rJn-A6i6V9ScQu5Me0fGstd0vO3Xe8u0e7kqnOiuuTe8lz-QvbQMPd8y4SQqQdqh828rq2L735x6UbgSgMJNxwoeojjojYkOX5WJoV72E8M0VawzH3324.7XlALisa44at8eO7YTFpz0Z3yjoV3H6Uys9ev3YqHJQ&dib_tag=se&keywords=modern+technical+writing&qid=1772684162&sprefix=Modern+technical%2Caps%2C122&sr=8-1)
## FAQ
### Why use Markdown instead of writing HTML?
Markdown is easier to read and write than HTML. It allows writers to focus on the content rather than formatting details. Andrew Etter recommends lightweight markup languages like Markdown because they are simple, portable, and integrate well with documentation tools.

Markdown files also work well with version control systems and static site generators.

### Why don't my changes appear on the website after editing the Markdown?
This usually happens because the site has not been rebuilt.
If you are previewing the site locally you should run:
```
mkdocs serve
```
If the site is hosted on GitLab Pages, you must push the changes to GitLab so the automated pipeline can rebuild the website.
## Credits
Author

**Steve Kakina Mateso**

Peer reviewers

Jackson Gumprich, and Charles Ostrum

Tools used
* MkDocs static site generator
* Git distributed version control system
* GitLab Pages hosting platform

These tools were selected because they follow the workflow recommended by Andrew Etter in *Modern Technical Writing*, which encourages using lightweight markup languages, distributed version control, static site generators, and forges to publish documentation efficiently.