---
title: "Can't Perform System Administration"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by SkyDiver on 2006-02-19
Hi,

I'm very new to Ubuntu.  I've had Mepis installed on a dual boot system for quite some time, but could never spend the time to figure it out.  Heard good things about Ubuntu, so here I am.

My installation seemed to go quite well.  I can play games, access the web, play with OpenOffice, etc.

My problem is that the system does not respond when I try to do anything to the system itself.  For instance, there are 31 updates available according to a red icon next to the sound icon in the menu bar at the top of the screen, but there appears to be no way to initiate the updates.  

I just tried to run Synaptic Package Manager.  It lets me put in my password, but then nothing else happens.  Was my password valid?  I don't know.  Nothing happens.  This is the same problem when I try almost anything other than using apps that are already installed.

Here is another one.  I just tried to open System/Administration/Services.  (Just to see what was there.)  At the bottom of the screen, it said it was opening them.  Then it disappeared.  No error messages or anything.  I don't know what happened.

I followed the instructions on this forum to open Automatix.  It looked like I was getting some feedback from the system.  It appears that it successfully downloaded, but when I tried to run it, Linux couldn't find the file.

So, although everything looks nice, I can't seem to get anything done.  Any help would be appreciated.  (It is almost 3AM here.   I'm going to bed, so I'll check on any replies in a few hours.)

  -- George

---

### Post by Netisan on 2006-02-19
IMHO, if you ever can see the updates you are already a superuser. The superuser default password is the same as your user password. I don't believe your problem adresses administration rights. Maybe you should more carefully read the menus and prompts..
Another isssue. Having "waiting" updates IMHO doesn't oblige you to install all of them. Or any of them. I have 57 pending updates but right now I dont want to spend traffic for them.

The same with Synaptic: if you ever open it, your su pass is OK. What you can do in Synaptic is to read the descriptions (bottom right) of the packages (top right), and to mark them with the right mouse button for installation or what you want. Execution of selected actions is via the "Apply" button at the top bar. 

You can even try a KDE package manager KPackage. It may be better for you.

---

### Post by SkyDiver on 2006-02-19
Is a superuser the same thing as the Root user?  I saw earlier posts which led me to believe that the Root user can only do things in a terminal or command line. 

Is that correct?  And if so, is that unique to Unbuntu vs. Mepis, for instance?

I was just concerned that a lot of the menu functionality doesn't seem to work and doesn't tell me why.  

Thanks.

---

### Post by nalmeth on 2006-02-19
In Ubuntu the root user is disabled by default. Ubuntu uses a program called sudo to attain administration priviledges when needed. It is a security precaution, as you don't want to run around doing everything as root like in windows

When you installed automatix you did:
wget [http://beerorkid.com/automatix/automatix_5.4-3_i386.deb](http://beerorkid.com/automatix/automatix_5.4-3_i386.deb)
sudo dpkg -i automatix_5.4-3_i386.deb

in a terminal right?

Are you using KDE or GNOME?
If gnome, to run automatix go APPLICATIONS --> SYSTEM TOOLS

Hit the reload button in synaptic, I think that fetches updates for you, and offers to install them. If you'd like, you can just do this in a terminal instead:
sudo apt-get update
sudo apt-get upgrade

---

### Post by Netisan on 2006-02-19
[QUOTE=SkyDiver]Is a superuser the same thing as the Root user?  I saw earlier posts which led me to believe that the Root user can only do things in a terminal or command line. 

Is that correct?  And if so, is that unique to Unbuntu vs. Mepis, for instance?

I was just concerned that a lot of the menu functionality doesn't seem to work and doesn't tell me why.  

Thanks.[/QUOTE]
The superuser is not exactly root user, but it's enough to administer the system. For terminal and command line superuser is OK. In fact, you don't need to be root if you don't administer other users (IMHO) on your machine. 
Please, share your real problems with installation, if any.

---

### Post by SkyDiver on 2006-02-19
**nalmeth**,
So root is equivalent to an administrator in WinXP?

I'm using Gnome.

Regarding Automatix, the text you show looks like what I did.  I copied and pasted the text from the post in this forum into a terminal.

I know that it downloaded, but it doesn't show up in my System Tools.

What is confusing to me is:  Do I have to be a su to use the System Tools?  And can I be a su outside of a terminal?

**Netisan**,
I think I'm OK.  I mean, I don't have any real installation problems if this is not a problem.  I'd like to be able to change my screen resolution and things like that, but I don't know if I have the rights to do that under my normal username.

Oh, sometimes it will ask me for my password.  In those cases, it doesn't say whether it is my user p-word or root.  I assume if it doesn't specify, that it is the user p-word.

Are these dumb questions?  (I actually build my own XP systems and use lots of powertoys in that environment.  I feel like a big time n00b here!)

---

### Post by nalmeth on 2006-02-19
> So root is equivalent to an administrator in WinXP?
precisely
> 
I know that it downloaded, but it doesn't show up in my System Tools.
hmm, can you execute automatix from the terminal? Are you sure you did the 'sudo dpkg -i automatix_5.4-3_i386.deb' part? Wget just downloaded the package. dpkg does the dirty work

> Do I have to be a su to use the System Tools? And can I be a su outside of a terminal?

Really the only way to be su outside of a terminal, or outside of a situation where you are asked for your user password, is to create a root user, and log in with it. So you can start all the system tools as user, but you will be prompted for your password when it is needed.

> Are these dumb questions? (I actually build my own XP systems and use lots of powertoys in that environment. I feel like a big time n00b here!)

No dumb questions, it might just be harder to adjust to a new system when you're already engrained with experience from another. I am no programmer or admin or anything. Just an end-user whose taken time to learn. Ubuntu probably cut the learning curve in half for me, and once you get used to the surroundings, you will catch on quite quickly!

Use the forum to the full extent. Whatever problem you run into, someone has probably run into it before. Person to person communication helps greatly, even if its not live convo!

happy ubuntuing!

---

### Post by SkyDiver on 2006-02-19
Thanks for all your help, guys!

---

### Post by ShackletonEH on 2006-02-21
I am also having a problem with Synaptic. I cannot get it to open (at all!) When I click on it from the Administration menu, nothing happens! I have also tried adding applications from the Applications menu. That too does not open anything either!

   I also see the red ball (top right of screen) indicating that there are updates avaiable but when I cick on the install updates option, again nothin happens! What should I do?

---

