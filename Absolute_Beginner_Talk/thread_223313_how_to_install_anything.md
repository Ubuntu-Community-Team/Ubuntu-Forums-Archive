---
title: "how to install anything?"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by saumya on 2006-07-26
Hi,I a a newbe here.I just installed UBUNTU v5 I think, not sure and definetely not draper drake.
My question is general, I am quite used to install/uninstall programme of windows.But here in linux I could not able to install anything.I ahve dowmnloaded things like firefox (upgraded version),  then flash player, then apache, but could not bale to install anyof them.Whats the general procedure to install such things. I ahve downloaded for linux versions of these things.

---

### Post by Jagot on 2006-07-26
This is a pretty good link for installing packages:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Always check if the program you're trying to download is available in the repositories (via Synaptic) before trying to download files separately.

You may also want to have a look at Automatix for Breezy - may be able to install a few things that you need:

[http://getautomatix.com/wiki/index.php?title=Automatix_for_Breezy](http://getautomatix.com/wiki/index.php?title=Automatix_for_Breezy)

---

### Post by kabus on 2006-07-26
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by richardward101 on 2006-07-26
firefox should take care of itself in ubuntu, you shouldn't need to download it especially if you're running dapper.
If you want to get from where you are to running dapper, type the following in a terminal:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

you'll be asked for a password, its the one you gave when you installed.

Check out the links above they'll answer your installing question, but I must recommend [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper) for how to get flash player working.

---

### Post by 3rdalbum on 2006-07-26
> **richardward101 said:**
> firefox should take care of itself in ubuntu, you shouldn't need to download it especially if you're running dapper.

I must recommend [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper) for how to get flash player working.

The original poster specified that he was using either Breezy or Hoary.

Firefox will not automatically update to 1.5 in Breezy/Hoary; you will need to search for a Howto on that or upgrade to Dapper.

---

### Post by justicerulesok on 2006-07-26
I am a noob at all of a week old.  This might help...

**To download softwar**e go to 'System' 'Administration' 'Synaptic Package Manager' where you can perform a search for either a specific program or a type  of program (IE you could look for web browsers or specifically lynxx).  You may get a message telling you it not available under the website for your release but is available from the universe to which you agree.

**To install downloaded or optional bundled software** go to 'Applications' 'Add/Remove' and again search for your program which you can then install.  Ubuntu does not need to be restarted.

**To install manually or run scripts** you need to go to 'Applications' 'Accessories' 'Terminal' which is like a DOS command window.

Ubuntu does not allow users to log on as the root owner (administrator is a normal account I created).  As such you need to run the sudo command when / if you get a permission denied file or are following instructions that have been posted online.  To run the sudo command you simply type 'sudo ' before you then write (or copy and paste) each line of instruction, be careful to ensure if copying and pasting that you type sudo first & then paste in only one line then repeat.  This is because some lines run as soon as you paste without needing you o press enter.

I hope it helps - I wrote it for my boss!

Justice.

---

### Post by richardward101 on 2006-07-26
> **3rdalbum said:**
> The original poster specified that he was using either Breezy or Hoary.

Firefox will not automatically update to 1.5 in Breezy/Hoary; you will need to search for a Howto on that or upgrade to Dapper.

No indeed, thats why I was recommending the upgrade to dapper, didn't make it as clear as I meant to perhaps.

To surmise: read the installation tutorial (its quite easy going), and its probably for the best to upgrade to dapper in the manner specified in my post.

---

