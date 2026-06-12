---
title: "Question about Ubuntu's automatic updates"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by mr.v. on 2007-02-05
Hi all--

sorry for the trouble. I've come from Slackware so I'm not used to much in the way of package management help or automatic updates =)

I'm using 6.06.1. I have a question about Ubuntu's Update Manager. First of all, I want to configure Ubuntu so that it automatically downloads updates for the system and installs them without anyone having to enter the root password. I have found (somewhat unintuitively) that the settings for "Update Manager" are actually in System|Administration|"Software Properities"

Anyway, there appear to be two conflicting settings, both of which can be simultaneously checked under "Internet Updates" tab.
Check for updates daily goes without saying...however then there are two others:
"Download updates in the background, but **do not install them**"
and "Install security updates without confirmation"

sooo...if the "Download updates in the background" is checked will it refuse to install security updates even though the "install security updates" is checked because it "does not install them"? 

Alternatively...if the "install without confirmation" is checked does it require the Download updates to be checked or will it automatically download any security update and install it regardless of the status of "Download updates"?

The other question I have is, is it possible to determine what packages will and will not be updated on a per-package basis?

Really here's the reason. I want to use my own kernel and keep it and glibc stable (barring some obvious memory leak/security hole issue being discovered), and I don't want the updates to keep forcing me to reinstall them. Is it possible to tell the Auto updater to neglect updating these two things but keep updating things like OpenOffice/mplayer/etc without confirmation?

If so is there a good resource on where to do that? I tried googling and searching these forums but I'm not finding what I'm looking for. Sorry for the trouble.

Thanks for the help!

---

### Post by az on 2007-02-05
> **mr.v. said:**
>  is it possible to determine what packages will and will not be updated on a per-package basis?!

Yes, of course.  You can unselect the ones you don't want.

> **mr.v. said:**
> 
Really here's the reason. I want to use my own kernel and keep it and glibc stable (barring some obvious memory leak/security hole issue being discovered), and I don't want the updates to keep forcing me to reinstall them. Is it possible to tell the Auto updater to neglect updating these two things but keep updating things like OpenOffice/mplayer/etc without confirmation?


You can lock the version of a package on your system using synaptic.

---

