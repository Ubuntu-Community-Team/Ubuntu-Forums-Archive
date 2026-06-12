---
title: "backup and root privileges"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by Victoriakhf on 2007-06-23
Hi,

I downloaded the upgrade to Fesity (hoping it would take less time than the ISO) so now I'm wondering if there's a way of backing it up?

Since I'm the only one to have access to my computer- is there a way (and is it safe) to automatically allow myself root user privileges?

Thanks

V

---

### Post by coffeecat on 2007-06-23
> **Victoriakhf said:**
> Since I'm the only one to have access to my computer- is there a way (and is it safe) to automatically allow myself root user privileges?

Since you are the sole user, you already have root user privileges. [This link explains all.]("https://help.ubuntu.com/community/RootSudo")


> **Victoriakhf said:**
> I downloaded the upgrade to Fesity (hoping it would take less time than the ISO) so now I'm wondering if there's a way of backing it up?

Fesity, eh? :wink: Makes a change from Fiesty. Anyway.... I'm not quite clear what you're saying. Have you upgraded Edgy to Feisty? If so, all the deb files that comprised the upgrade should still be in /var/cache/apt/archives and you could copy them to a backup medium if you want. Trouble is, most/all of the other .deb files you've ever installed will still be sitting there, unless you've done a clearout. Happy sorting!

**Edit:** If you mean backing up the whole installation, that's a different matter. Just search the forums - there have been plenty of threads. Or post back. :)

---

### Post by Victoriakhf on 2007-06-24
HI - thanks

Re: root-  what I'm getting is - I've put firestarter in startup, but I get "insufficient privileges" message. I looked in users and groups and the "root" has no user privileges ticked - is that my problem?

Backup - yes I mean the whole installation really - so I can reinstall, cos I'm going to upgrade my hard drive soon. I have looked in the forums, but can't seem to find what I'm looking for!:confused:

---

### Post by shifty_powers on 2007-06-24
Try having a look at:

[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

Hope that helps ;)

---

### Post by coffeecat on 2007-06-24
> **Victoriakhf said:**
> Re: root-  what I'm getting is - I've put firestarter in startup, but I get "insufficient privileges" message. I looked in users and groups and the "root" has no user privileges ticked - is that my problem?

You don't have to put firestarter in startup. There's a common misconception about firestarter induced, no doubt, by concepts from the Windows world. Firestarter is not a firewall per se, simply a gui configuration for IPtables which is the real firewall. If you've installed firestarter there should be a gnome menu entry somewhere. Possible System > Administration but I can't be sure. I'm in Gentoo atm and can't check where Ubuntu puts it.

Anyway, startup firestarter from there, enter your ordinary password when prompted and follow the very simple wizard. This will create a basic iptables configuration file which will be followed whether firestarter is running or not. It's much friendlier than editing iptables by hand. Have a quick look [at this]("http://gentoo-wiki.com/HOWTO_Iptables_for_newbies") and you'll see what I mean. Then take a couple of aspirins and go and have a lie-down to recover. :lol: 

If you need more complex rules, such as allowing ssh-ing, use the events or policy tabs. Simply close firestarter down when you don't need it - this worries a lot of people, but the firewall is still active.

I have one piece of bad news though. The firestarter project is dead upstream - has been for a couple of years now. It is causing problems with certain parts of the code in later kernels and this issue will only get worse. A time will come when it will be pulled from the repositories - this has already happened in Gentoo. It's a great pity. There are several other GUI frontends for iptables but none are so user-friendly as firestarter - imo.

**Edit:**, just to add an alternative to the previous poster's excellent suggestion - have a look at [Partimage]("http://www.partimage.org/Main_Page"). Personally, I don't like it but a lot of people speak highly of it. My own preference is to use tar from the command line. Simple, easy and quick but you have to be comfortable with the cli.

---

### Post by Victoriakhf on 2007-06-25
Thanks people - that's me sorted then.:)

Did wonder about Firestarter, cos when I try to restart from hibernate (doesn't seem to like to like that very much...) it says "starting firestarter" anyway.

Should have thought of a "ghost", so many thanks for that too.

V

---

### Post by carloslosgrande on 2007-06-25
Hi. I'm not sure if this is what you want but I use it all the time to keep my current setup - for when I do something silly and stuff everything up.
This is courtesy of UbuntuGeek

> Ubuntu Tricks - how to generate a list of installed packages and use it to reinstall packages

This tutorial will work for any Debian based system, but is written specifically for Ubuntu.
I’ve recently had the occasion to make a complete list of software installed on one of my Ubuntu boxes, and then reinstall it from scratch. Here’s a quick and easy way to generate a list of installed .deb packages, and then use that list to quickly reinstall them.
digg_url = 'http://digg.com/linux_unix/Ubuntu_tricks_how_to_create_a_list_software_and_use_it_to_restore_your_pc';
First, let’s make the list. You’ll be doing all of this in a Terminal Session:
dpkg --get-selections | grep -v deinstall > ubuntu-files
NOTE: Wordpress interprets two dashes (- -) as one dash (–). When you’re putting this into your CLI, make sure it’s dropping two dashes ‘- -’ without the space between them.
Now you’ve got a list of all of your installed debs in a fairly small file. In my case, I simply moved this file to a thumb-drive. You could also store it on a seperate partition or on a disk somewhere. Heck, it’s not that big, email it to your gmail account.
So now you’ve got this list and all is well, until you’re Ubuntu install either dies or has to be reinstalled for some reason. Go ahead and do the base install.
Once you’ve got Ubuntu back up and running, copy your ubuntu-files back into your home directory and do the following:
sudo apt-get update
sudo apt-get dist-upgrade
sudo dpkg --set-selections < ubuntu-files

NOTE: Wordpress interprets two dashes (- -) as one dash (–). When you’re putting this into your CLI, make sure it’s dropping two dashes ‘- -’ without the space between them.
Now you’ve told your system what it needs to install, so let’s install it all.
sudo dselect
This will open up a dselect session. Type ‘I‘ and allow dselect to install of the the packages listed in your ubuntu-files document. When it’s finished, type ‘Q‘ and hit the ENTER key to exit dselect.
Now you’re a lot closer to where you were before.
geek out.
I run this every week and copy it, and my files,  to ext HDD and Bob's my uncle.
Simple.

---

### Post by coffeecat on 2007-06-25
> **Victoriakhf said:**
> Did wonder about Firestarter, cos when I try to restart from hibernate (doesn't seem to like to like that very much...) it says "starting firestarter" anyway.

Just to clarify - I simplified what I was saying about firestarter slightly. When you install firestarter an init script for firestarter is added which is invoked when you boot up. See under /etc/init.d. Tbh I'm not exactly sure what this does because I thought Iptables did the real work. But anyway, this is why you don't need to add firestarter to System > Preferences > Sessions (I presume that's what you did) and why you see firestarter mentioned after a restart.

---

### Post by Victoriakhf on 2007-06-29
I forgot - I also can't move stuff into filesystem - like I said before - root doesn't have any user privileges selected in "users and groups" - should I select them?

Thanks

---

