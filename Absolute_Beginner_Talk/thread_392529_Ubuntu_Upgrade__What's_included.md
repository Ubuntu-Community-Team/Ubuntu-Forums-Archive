---
title: "Ubuntu Upgrade / What's included?"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by justaboutnormal on 2007-03-24
I am eagerly awaiting the new release of Ubuntu 7.04 next month, but I have a few questions.  I first started using Ubuntu a month or so ago and so I'm not sure what will be upgraded when I upgrade.

Ubuntu Feisty has added desktop effects and some new packages/ programs, and I want to know if these are all included when you type: sudo aptitude dist-upgrade.

---

### Post by Arby on 2007-03-24
When you upgrade from Edgy to Feisty you will get the new versions of all the packages you currently have installed. You won't get new packages being installed by default. So for example if you don't currently have 3d desktop effects (beryl/compiz) installed then they won't suddenly be installed when you move from edgy to feisty, you'll have to install them afterwards.

When people say that feisty includes desktop effects by default it means that they will be available in the ubuntu official repositories, not that they will be automatically installed. If you really want to know exactly what will be upgraded try this command```
sudo dpkg --get-selections >package_list
``` that will create a file in your home directory called package_list. It contains a list of all the packges you currently have installed. When you upgrade from edgy to feisty you will get the newest versions of all those packages.

---

### Post by justaboutnormal on 2007-03-24
So, any of the packages from the next Ubuntu that I want I will have to manually install, right?

---

### Post by Arby on 2007-03-24
Broadly speaking yes, it depends what you mean by 'new'. In terms of end user applications and desktop stuff my understanding is that if you want an application from feisty that you do not currently have in edgy then yes you will have to install it. On the other hand there will may be new components in the internals of the OS that will change without you ever needing to know about it. It's quite hard to give a hard and fast answer to this, you'd really need a developer or someone with greater knowledge than me for that.

Did you have a specific example in mind? Let me give one. Edgy had OpenOffice 2.0 Feisty has Open Office 2.2. that sort of change will happen automatically. In contrast, during the transition from Dapper (Edgy -1) to Edgy to Feisty Ubuntu is going through the transition from init to upstart. Init is the very first process that starts when you boot your machine and controls the startup of all subsequent processes. Upstart is a completely new program that does the same job. This transition would happen automatically under the hood even though it involves the installation of a new program.

When the final release of feisty occurs there will be an official upgrade process to handle the transition as smoothly as possible. Upgrades between releases is a complex process. If you have a specific example in mind it would be easier to explain.

---

### Post by justaboutnormal on 2007-03-25
That sounds good. I just wanted to know in general what to expect.  Thanks.

---

### Post by tux_rox on 2007-03-25
Can you install Feisty on top of Edgy pain-free (you don't lose all of your data, just get the new stuff?)

---

### Post by Chappy7777 on 2007-03-25
> **tux_rox said:**
> Can you install Feisty on top of Edgy pain-free (you don't lose all of your data, just get the new stuff?)
Good question, tux_rox. I'm a noob myself so don't give any credence to this reply.

However, my guess is that you will need to do a HDD reformat and thus, be starting from scratch.
If this is the case, back up your Bookmarks from FFox, and whatever else you can. Burn to CD or copy to a Floppy if you still have an A Drive. I use a sight called [www.box.net](www.box.net) that allows me to save 1 Gig of info online. 1G is plenty for addresses, boolmarks, etc.

I'm looking forward to an educated answer to your question.

Chappy

---

### Post by jeffathehutt on 2007-03-25
Well, in theory you can install feisty over edgy without losing anything (once feisty becomes stable).  The upgrade process is designed to keep all your files and settings after the upgrade.

But, in the real world things don't always go smoothly, so before you decide to upgrade to feisty, make sure you have backed up any important files.

---

### Post by Kamu on 2007-03-25
Actually, in theory, you can upgrade to a new version of the distro directly using apt with a few simple terminal commands, editing one file (the list of your repositories) and some patience if you do not have all that much bandwidth.

However, historically, updating the distro directly has been more error prone for users than installing from scratch, so it is definitely recommended to backup all the contents of your home directory and all other files that are important to you before proceeding with the direct upgrade.

---

### Post by Arby on 2007-03-26
A good bit of general advice is to set up your system with your home directory on a separate partition of your hard drive. You can do this during the disk partitioning step of the install. Most of your personal settings are stored in your home directory in hidden files, along with all your personal data files. I still have the same home directory I had when I installed Dapper. This laptop currently has both edgy and feisty installed and both use the same partition as their home directory. This means I have access to the same files and settings regardless of which version I'm currently using. There can be occasional conflicts when different versions of an application require slightly different settings but these are rare and mostly trivial.

Doing a fresh install is often less hassle than a direct upgrade, although a lot of work is currently being done to make the direct upgrade tools 'just work'. If you have your home directory on a separate partition then as long as you are careful not to reformat this partition during the install you get to keep all your data files, settings and bookmarks etc with minimal trouble.

Of course it's still a good idea to take regular backups of your home directory, just to protect yourself against disasters. If anyone doesn't have their home directory on a separate partition it might be worth taking the time to set it up this way when you make the shift from edgy to feisty. It could save trouble in the long run

Of course this is just my opinion, take it or leave it :) 

Arby

---

