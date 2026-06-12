---
title: "Help upgrading from Feisty (PPC)"
date: 2009-09-06
forum: Apple Hardware Users
---

### Post by megabenman on 2009-09-06
So I completely forgot I had a 40 GB Kubuntu Feisty partition on my iMac G5 (I had gotten so used to pressing 'x' at the boot screen I forgot I had linux).  Today is the first day in probably a couple years that I'm really using it, and I'm having a few problems.
1.  I'm still using Feisty 7.04 which I assume is old by now.  I tried googling to upgrade to newer versions but adept manager crashes everytime.
2.  Still using KDE 3.5.6, but I assume it gets upgraded when upgrading Feisty?
3.  I finally got my wireless internet working on this machine but I'm worried an upgrade will force me to lug my iMac downstairs once again, just to plug it into the router so I can install updates required for wireless compatibility
4.  I remember finding a thread a while ago that helped get my wireless apple mouse and keyboard to connect at startup, but now that I want to connect my somewhat new wireless mighty mouse, I can't find the thread.  Any help?

---

### Post by rjcalifornia on 2009-09-07
Well, why won't you try Kubuntu 9.04 Live CD? To run it, type this:

live-nosplash-powerpc

It's gonna take some time, so don't touch anything ;)

Here's a tutorial, in case you want to install it:

[http://ubuntuforums.org/showthread.php?t=1114297](http://ubuntuforums.org/showthread.php?t=1114297)


Cheers, and keep us updated!

---

### Post by gunksta on 2009-09-08
Yeah, Feisty is a little old. To upgrade to the current version of Kubuntu, I would recommend dropping to a tty terminal and entering these two commands.

sudo apt-get update

sudo apt-get dist-upgrade

To get to a tty press Ctrl-Alt-F1. This should take you to a black screen with white text. You will need to log-in again to enter the commands (write them down first).

If apt-get asks you any questions, go with the defaults. They are probably correct. You may be able to do this from konsole (the command-line app in Kubuntu) but the dist-upgrade part will involve replacing basically everything on the computer. In many cases, there have been significant changes since Feisty was released (KDE is now in the 4.x series of releases as opposed to the 3.x series for example).

When the dist-upgrade gets finished (hopefully with no errors) you need to:

sudo shutdown -r now

This will reboot your computer.

I have absolutely no idea how well this will work. Feisty is old and I have no idea how many tests were done against Feisty as a source for an upgrade to the current version.

A fresh-install (see RandyVanBuren's post) is probably a better idea.

---

### Post by megabenman on 2009-09-08
I'm having a problem with the tty terminal.  Whenever I try to type the command, it asks me for my password.  I type in the passsword but everytime it tells me "login incorrect"
Why is this?

---

### Post by khelben1979 on 2009-09-08
> **megabenman said:**
> I'm having a problem with the tty terminal.  Whenever I try to type the command, it asks me for my password.  I type in the passsword but everytime it tells me "login incorrect"
Why is this?

Probably because you're inserting the wrong password. Every command which is used by sudo requires the super user password from that system. It wouldn't surprise me if the password for your default user don't use the same password.

---

### Post by megabenman on 2009-09-08
Ahaha damn :P
Well I don't remember changing the system password, so what's the default?

---

### Post by gunksta on 2009-09-08
Before you type the commands, you have to log in.

You MUST enter your user-name and password. You would have set these when you first installed Kubuntu. There is no default.

Once you log in, you can type in the commands from my earlier post. Enter them one at a time (we're not going to get fancy today and enter them together).

After you enter the commands, Kubuntu is going to ask for your password. You should enter the same password that you gave when you logged in to the system.

All of this assumes that this is a basic Kubuntu installation and that you are logging in as a user with the ability to escalate your privilege to root, to perform system tasks (the previous statement is an over-simplification, but will do).

It looks like you know your password since you are able to log in via the fancy-pants log-in manager. You need to use the same user-name and password here.

I hope that makes more sense.

---

### Post by rjcalifornia on 2009-09-08
> **megabenman said:**
> Ahaha damn :P
Well I don't remember changing the system password, so what's the default?

Sorry, there's no default.... How about a fresh install?

---

### Post by megabenman on 2009-09-09
I figured out how to use tty but the upgrading commands gave me errors.
I'm looking everywhere for a PPC Kubuntu LiveCD (should be 64bit also...) but can't find it anywhere.

---

### Post by gunksta on 2009-09-09
I owe you an apology. You clearly stated in your first post that you are running a G5, but I over-looked that fact.

You can get a download from here:

[URL="https://wiki.ubuntu.com/PowerPCDownloads"]https://wiki.ubuntu.com/PowerPCDownloads
[/URL]
I suspect you are getting errors because your sources list is no longer accurate. The last few releases have left PPC support to the community and are no longer maintained/supported by Canonical.

To upgrade via the command-line you would need to find a mirror that still supports PPC and direct your sources list to that mirror.

It's probably easier to just download one of the 9.04 CDs and upgrade that way.

---

### Post by megabenman on 2009-09-09
Yeah I remember PPC becoming community-supported a while ago... I figured that is why the command line wasn't working
I'm still stuck though, I can't find a PPC live cd download of kubuntu (or ubuntu for that matter) anywhere

---

### Post by gunksta on 2009-09-10
Umm.

My last post contained a link. 

:popcorn:

Lice CD, Alternate CD, the works.

---

