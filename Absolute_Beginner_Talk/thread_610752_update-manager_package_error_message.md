---
title: "update-manager package error message"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by mkarthik on 2007-11-12
'E:Problem parsing dependency Depends, E:Error occurred while processing libgail-common (NewVersion1), E:Problem with MergeList /var/lib/dpkg/status, E:The package lists or status file could not be parsed or opened.'

got this error message while trying to update using the update-manager package. Could somebody tell me what needs to be done?

---

### Post by overdrank on 2007-11-12
> **mkarthik said:**
> 'E:Problem parsing dependency Depends, E:Error occurred while processing libgail-common (NewVersion1), E:Problem with MergeList /var/lib/dpkg/status, E:The package lists or status file could not be parsed or opened.'

got this error message while trying to update using the update-manager package. Could somebody tell me what needs to be done?

HI, what version of ubuntu are you using, Feisty, Gutsy? And please post the out put of these commands in the terminal ```
sudo apt-get update
sudo apt-get upgrade
``` The terminal is located under applications, accessories.

---

### Post by mkarthik on 2007-11-12
i'm using gutsy...

and i get pretty much the same error message when i run the two commands

E: Problem parsing dependency Depends
E: Error occurred while processing libgail-common (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

so i tried opening the /var/lib/dpkg/status file .... it worked in vi .... gedit threw errors about character encoding..

do you think i need to regenerate this file?

---

