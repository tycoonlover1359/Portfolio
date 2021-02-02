# Personal Portfolio
This is a collection of projects I've undertaken over my programming time, usually on my own. These projects generally don't have official repositories, as it wasn't until the making of this document that I thought of publically releasing my code; generally, before this, I always had the mindset of "Why would anyone want to use, or even look, at my code!? It's terrible", since I generally thought of my code as pretty bad due to me lacking in experience (given that I've only been programming in any "official" capacity for just less than one year).

# Legend
- **Active** - The project is actively used by me (and possibly others, such as friends) with at least semi-regular updates (both feature and security).
- **Active-ish** - The project is actively used by me (and possibly others), but few updates happen and only if necessary.
- **Inactive** - The project is semi-actively used by me (and possibly others), but updates usually don't happen and only if necessary; these are projects I may revisit in the future but are not yet "abaondoned."
- **Abandoned** - The project is rarely, if ever, used in its current state, and there are no plans to update it for any reason.

# Projects
| Name | Status |
| ---- | ------ |
| [Failed Labs Discord Bot](#failed-labs-discord-bot) | Abandoned |
| [Minecraft Security System](#minecraft-security-system) | Inactive |
| [Personal Website](#personal-website) | Active-ish |
| [SCiPNET Terminal](#scipnet-terminal) | Inactive |
| [SlackMail](#slackmail) | Active-ish |
# Failed Labs Discord Bot
A planned Discord bot that was never officially announced or released. Intended to be a custom built bot that handled all required tasks of a friend's Roblox and Discord group: Failed Labs. Built in Python using `discord.py`, it utilized Amazon Web Services as its main data backend (database and storage) and served as the main way I learned what I know about Python. The project has since been abandoned due to a lack of enthusiasm in advertising or otherwise "starting up" the group.

| Item              | Link                                                           |
| ----------------- | -------------------------------------------------------------- |
| Language          | Python                                                         |
| GitHub Repository | https://github.com/Failed-Laboratories/Failed-Labs-Discord-Bot |

# Minecraft Security System
This is a security system for Modded Minecraft designed to use websockets to communicate with the back end. This is intended to be used with ComputerCraft, though could be adapted to be compatible with OpenComputers. The clients were built using ComputerCraft Lua, and the back end was built using Python. Data related to each security system network is stored in Amazon DynamoDB, with Amazon API Gateway handling connections and routes, and AWS Lambda handling the back end authentication and route logic (what each route is supposed to do). The project is projected to be fairly inexpensive (though not necessarily free) with just one or two networks connected 24/7, however more networks (and/or rapid command usage) can impact costs incurred. 

| Item              | Link                                                         |
| ----------------- | ------------------------------------------------------------ |
| Language          | ComputerCraft Lua, Python                                    |
| GitHub Repository | https://github.com/tycoonlover1359/Minecraft-Security-System |
# Personal Website
My personal website, hosted on [HelioHost](https://heliohost.net) and accessible at https://tycoonlover1359.omg.lol/. Built using Python and Flask, it is a relatively simple website that tells people a little bit about myself, including my interests, the languages I know, and the services I have experience with. It also features (an as of publication, unused) blog function that uses Amazon S3 to store blog posts (since HelioHost limits their free storage to 1 GB per person, though it is expandable by donating to them). The site also uses Amazon Simple Email Service in combination with AWS Lambda to handle alerting people that I've received their message to me (messages sent via the contact form at the bottom of the home page). The website is then served via either HelioHost directly or the [Arc.io](https://arc.io/) peer-to-peer CDN, the latter of which pays me small amounts as people view the website.

The idea in the future may be to write little (or large, who knows?) guides about things that interest me, namely Amazon Web Services (hence the inclusion of the Arc.io CDN, as it would allow me to earn *some* money without serving ads, which I hate just as much as basically everyone else does).

Sidenote, the domain I use is from the folks over at https://omg.lol/, made by [Neatnik, LLC](https://neatnik.net/). They did not give me the domain for free (I bought the domain with my own money), but I have become acquaintances with the owner. While *technically* a subdomain, `omg.lol` is registered on the Public Suffix List, and thus, for most intents and purposes, can be treated as any other top-level domain (i.e., `.com`).

This project is technically maintained, as I use it to handle webhooks during testing whenever I don't want to use Amazon API Gateway to handle the webhook request (such as seeing, for the first time, what Slack `POST`s to designated webhooks upon buttons being clicked).

| Item              | Link                             |
| ----------------- | -------------------------------- |
| Language          | HTML, CSS, JavaScript, Python    |
| Link              | https://tycoonlover1359.omg.lol/ |
| GitHub Repository |                                  |
| Domain Registrar  | https://omg.lol/                 |

# SCiPNET Terminal
A little web "toy" of sorts that I made mainly as a roleplay device for my friends and I to use when roleplaying as SCP Foundation staffers (when/if that ever happens again). Made using [jQuery Terminal](https://terminal.jcubic.pl/) by jcubic, the app basically acts as a front end to a Python Flask server (also hosted on HelioHost). Commands (and their parameters) are sent almost directly to the server with little (if any, for some commands) action taken by the front end; the server handles much of the heavy lifting, including interacting with Amazon S3, which is where SCP articles are stored (due to the terminal's custom formatting, each article must be added individually to be stylized correctly; though I'm sure there are programmatic ways of handling this, I just wasn't sure if the effort required to do this was worth it).

This project is not often used, but is still fun for me to play with, so I sometimes add new documents and make some improvements (the latter generally adding/editing commands that only print text).

| Item              | Link                             |
| ----------------- | -------------------------------- |
| Language          | HTML, CSS, JavaScript, Python    |
| GitHub Repository |                                  |

# SlackMail
A mainly back-end-based system that handles reciving email to any email address with the `tycoonlover1359.omg.lol` domain; in other words, emails addressed to `tycoonlover1359@tycoonlover1359.omg.lol`, `hello+world@tycoonlover1359.omg.lol`, etc., are all handled by this system. SlackMail simply handles the emails after they've been placed in Amazon S3 by Amazon Simple Email Service. SlackMail will download the email from Amazon S3, parse it for who sent it, what address received it, the subject line, and date and time received. SlackMail then saves this email to a more sensible location in Amazon S3 (i.e., `tycoonlover1359.omg.lol/hello/world/` instead of simply `asdflkjasdflakj13lkj123lkj.eml` in the bucket's root directory) and sends a message to a Slack channel containing who sent it, where it was received, and the subject line, along with buttons to allow me to download or delete the email.

SlackMail currently does not have the ability to use Amazon SES to *send* emails, however such a function could fairly easily be built using AWS Lambda (I just have done so yet because I haven't yet needed to send from my custom domain).

This project, whlie not exactly maintined in any official capacity, is still used quite frequently by me as it is how I handle emails for services I sign up for (i.e., my Roblox account has its own email, my Discord account has another, different, email, etc.)

| Item              | Link                             |
| ----------------- | -------------------------------- |
| Language          | Python                           |
| GitHub Repository |                                  |