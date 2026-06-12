---
title: "Ubuntu and Slackware/lilo?"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by charger on 2007-03-21
Hi,

I'm a slackware user and would like to try out Ubuntu. My question is:

I am currently running Slack 11 on partition sda2 and have another partition sda1. I would like to try Ubuntu on sda1. Will the installer play nice with Lilo and my existing Slackware install? can I install Ubuntu from within Slackware (ie. mount the iso and install to my free partition)

Any help is greatly appreciated.

Thanks

Miguel

---

### Post by Bachstelze on 2007-03-21
If I were you, I'd install GRUB since it is IMO much more convenient than LILO. If you want to keep LILO though, it's very possible but you'll need an Alternate CD of Ubuntu - the Desktop one can only install GRUB on the MBR.

For installing Ubuntu fro within your Slack, see [here](https://help.ubuntu.com/community/Installation).

---

