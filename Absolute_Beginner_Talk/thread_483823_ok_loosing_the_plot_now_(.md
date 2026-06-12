---
title: "ok loosing the plot now :("
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by ROUBOS on 2007-06-25
Is there a way to remove everything that has to do with video drivers?
Completely remove everything and try from scratch again.

I have the ATI RADEON X800XT and I want to get my driver to work properly. I've tried so many different ways from posts in the forum and more, and I think that I have just managed to make a mess of it all.

Would like to just clean remove everything that has to do with the graphics drivers and try again.

Thanks

---

### Post by carloslosgrande on 2007-06-25
Hi, what I'm going to suggest may seem extreme but its a method I've used many times in just such situations.
Reinstall.
check out this care of UbuntuGeek;
> Ubuntu Tricks - how to generate a list of installed packages and use it to reinstall packages

This tutorial will work for any Debian based system, but is written specifically for Ubuntu.
I&#8217;ve recently had the occasion to make a complete list of software installed on one of my Ubuntu boxes, and then reinstall it from scratch. Here&#8217;s a quick and easy way to generate a list of installed .deb packages, and then use that list to quickly reinstall them.
digg_url = 'http://digg.com/linux_unix/Ubuntu_tricks_how_to_create_a_list_software_and_use_it_to_restore_your_pc';
First, let&#8217;s make the list. You&#8217;ll be doing all of this in a Terminal Session:
dpkg --get-selections | grep -v deinstall > ubuntu-files
NOTE: Wordpress interprets two dashes (- -) as one dash (&#8211;). When you&#8217;re putting this into your CLI, make sure it&#8217;s dropping two dashes &#8216;- -&#8217; without the space between them.
Now you&#8217;ve got a list of all of your installed debs in a fairly small file. In my case, I simply moved this file to a thumb-drive. You could also store it on a seperate partition or on a disk somewhere. Heck, it&#8217;s not that big, email it to your gmail account.
So now you&#8217;ve got this list and all is well, until you&#8217;re Ubuntu install either dies or has to be reinstalled for some reason. Go ahead and do the base install.
Once you&#8217;ve got Ubuntu back up and running, copy your ubuntu-files back into your home directory and do the following:
sudo apt-get update
sudo apt-get dist-upgrade
sudo dpkg --set-selections < ubuntu-files

NOTE: Wordpress interprets two dashes (- -) as one dash (&#8211;). When you&#8217;re putting this into your CLI, make sure it&#8217;s dropping two dashes &#8216;- -&#8217; without the space between them.
Now you&#8217;ve told your system what it needs to install, so let&#8217;s install it all.
sudo dselect
This will open up a dselect session. Type &#8216;I&#8216; and allow dselect to install of the the packages listed in your ubuntu-files document. When it&#8217;s finished, type &#8216;Q&#8216; and hit the ENTER key to exit dselect.
Now you&#8217;re a lot closer to where you were before.
geek out.

I back up my files and setup to ext hdd after running the first command.
I know some think this not the best way as it doesn't actually resolve the problem but it resolves it just fine for me.
Takes a while.

---

### Post by ROUBOS on 2007-06-25
thanks mate.
This is good to know. Good way to reinstall all the applications. Does this take care of multimedia codecs etc?

---

### Post by carloslosgrande on 2007-06-25
Hi, yeah it does. All the stuff you loaded to get your setup as it is now, is what will be loaded again.
I have ATI Radeon X600 and had similar problems with trying to get it working when I first got Feisty (prior to official release). Now the 'restricted drivers' works fine for me. But every so often I try something new and if it gets so messed up I can't fix.........then I do this thing.

---

### Post by Golyadkin on 2007-06-25
Good to know you don't always have to reinstal Ubuntu :)

---

### Post by carloslosgrande on 2007-06-25
Hi Golyadkin, less and less often. I'm almost to the stage where I know what I'm doing 10% of the time.:D

---

