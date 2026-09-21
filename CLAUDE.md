# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

**Project Overview** 

   Static HTML/CSS portfolio website deployed to AWS using S3 and CloudFront, provisioned with Terraform, and automated via GitHub Actions.

**Architecture** 

   Pure HTML5 and CSS3. 
   No JavaScript. 
   No build step. 
   No framework.

**Commands** 

 `terraform init`
  `terraform plan`
  `terraform apply`

**Conventions** 

   - All infrastructure changes go through Terraform — never modify AWS resources manually
   - No JavaScript in this project
   - CSS uses mobile-first approach with breakpoints at 900px, 768px, and 600px

   **Safety** 

   Never put secrets in this file. 
   No API keys, passwords, or AWS credentials.

## What this repository is

A static HTML/CSS portfolio website used as the deliverable for **DevOps Micro Internship (DMI) Week 1**. The exercise itself is about Linux basics, Nginx hosting, and deployment proof — the website content is secondary to that goal. There is no build system, package manager, bundler, or test suite; it's plain HTML/CSS served as-is.

## Working with this codebase

- No build/lint/test commands exist — there's no `package.json` or equivalent. Preview changes by opening the HTML files directly in a browser or serving the directory with any static file server (e.g. `python -m http.server`).
- `index.html` and `style.css` are the main site; `privacy.html` and `terms.html` are standalone pages with their own inline `<style>` blocks rather than sharing `style.css`. Keep that pattern if editing those two pages (don't move their styles into the shared stylesheet).
- Images referenced by the HTML/CSS live in `images/`; there is no image pipeline or optimization step.

## Mandatory ownership-proof rule

Per `README.md`, before this site is deployed, the footer in `index.html` **must** be edited to replace the original credit line with deployment attribution (name, cohort, group, week, date):

Original:
```html
<p>Crafted with <span>cloud</span> excellence by Pravin Mishra</p>
```

Replace with something like:
```html
<p><strong>Deployed by:</strong> DMI Cohort 2 | Student Name | Group 4 | Week 1 | 16-01-2026</p>
```

This proof must be visible in the deployment screenshot. If asked to help deploy or finalize this site, make/verify this edit first.

## Deployment target

The site is meant to be deployed on an **Ubuntu VM using Nginx**, served at `http://<public-ip>`, and kept live for 24 hours as part of the DMI exercise. Typical flow: copy the site files into Nginx's web root (e.g. `/var/www/html/`), restart Nginx, and verify via browser.
