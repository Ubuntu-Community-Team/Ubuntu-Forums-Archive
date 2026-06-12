---
title: "What are &quot;http AND ftp proxies&quot;"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by Dragon43 on 2007-02-06
I am so new and dumb.  What are [COLOR="Red"]http AND ftp proxies?[/COLOR]
Where do I need to put them?
Are they why I can't download [COLOR="Blue"]updates?[/COLOR]

Can somebody please 'splain to Lucy/Dragon43' in real small words.

Thanks.

---

### Post by ghandi69_ on 2007-02-06
I'm guessing that you are referring to your source list.  This is a file that tells ubuntu where to look to download programs, packages, libraries, and updates etc.....

This file is located in the etc/apt/ directory.  You can edit it using 

sudo nano sources.list 

or 

sudo gedit sources.list....

When you open that file, there should have already been a whole bunch of text there with a lot of http type addresses. Those are your sources. The first thing you should do to that file is uncomment out the address that have comments in front of them. A comment in the source file is the '#' character. Now, you can go through and do that if you like, or you can just make your sources.list file look like this by coping this in there.

Quote:
## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

## Listen
This information can be found from the starter guide(first link when typing "Getting Started With Ubuntu" into google. This can be a great source of information when starting.

---

### Post by steve.horsley on 2007-02-06
Some networks, mainly corporate networks, don't allow their users to connect directly to the internet. For users on these networks to get anything at all from the internet, they have to configure their PCs to speak to an intermediate machine that the company runs, and ask that to go get the info for you. These intermediates are called proxy servers. They have a connection to the corporate network and a connection to the internet. They may well do some content filtering and refuse or redirect your requests. They can also do caching (keeping a copy of info they have already downloaded for other people)  which can make downloading common files faster.

---

### Post by Dragon43 on 2007-02-07
But all I have between my Ubuntu computer and the satellite modem is a LinkSys router.
This Firefox works good.
My inhouse network works good.
So I don't have any proxys, correct?
My first attempt at running Ubuntu 6.06 , the update went fine, 200 + in that deal.  Now it says I have more and won't go there.So I added Automatrix and it won't fly either.

Physcocats will not fly on their directions either......

:::: cornfussed :::: ( does not take much, I am really not very good at this and need small words and pictures with lots of arrows on the back.)

---

### Post by steve.horsley on 2007-02-07
OK, so you don't have proxies. The question why you can't update remains. Can you try these commands and post the output?
[B]
sudo apt-get update
sudo apt-get upgrade[/B]

---

