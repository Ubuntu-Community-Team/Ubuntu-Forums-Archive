---
title: "What is the problem?"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-12-14
After several hours of frustration this morning, i'm turning here to hopefully figure out the problem at hand.
Last night I was trying to set up Thunderbird to work with my hotmail and university webmail account.  Everything was running smoothly when i went to sleep, but this morning I tried to get the same setup running on my girlfriend's computer.  To do this, i had to look at the settings i already had in my thunderbird, to use the same idea in hers.  During this, I guess i must have changed some sort of setting, because after clicking the "get mail" function, it would tell me that hotmail is not a real domain.  This is true, but i had a webmail extension running to take care of that problem.  As i said before, everything was running smoothly last night.  Also, when I attempted to write an email, it would tell me that it could not create the temporary file, and therefore would not send the email.  I have no idea what this error was, as I had never seen it before.  I decided that the best option was to delete all of the accounts I had in Thunderbird, and just start from scratch, whatever no big deal.  After doing that, and battling endlessly with the program to save the changes i was making (it didn't want to save my new account for some reason or another), I finally got it to accept my two new accounts (university webmail and hotmail).
 I checked my new account settings to my girlfriends (her's is working perfectly) and yet it still tells me that hotmail is not a real domain.
This is when things started to get weird.
I had been downloading torrents all night, and figured that maybe i had hit my bandwidth limit, as it's been a very common thing for me as of late.  Usually, an easy fix for this bandwidth problem is to plug in to an adjacent jack (in the university, this gives an entirely new ip address) or to just take the wireless approach.  I unplugged the internet cord going into my computer, and pressed the restart button.
Upon pressing the Red box (signifying the restart option) all of my panels disappeared, and i was left just looking at my desktop.  I could still change through workspaces, but nothing worked when i tried to open it.  I was left with just a desktop.
Manually restarting (holding down the power button) allowed me to boot up again, and get to the splash screen where i enter my username/password
I entered ubuntu as normal, but noticed i didn't have a network monitor (the two monitors in the panel telling me how my internet connection is; wired, wireless, etc)
I found it strange, but i just right clicked my panel and manually added the network monitor.  
Although I was not plugged in to any source of internet, my computer would still not attempt to join a wireless network (as it usually would if i wasn't plugged in).
After trying to open up a web browser, and just getting the "can not find page" error, i decided to plug in once again.
This is when the old network monitor decided to show it's face again, and now i had two network monitors on my panel (the new one i had added, and the old one that had been hiding)
This allowed me to access my home page, but i was still having errors, both with restarting and thunderbird.
Sometimes when i would open thunderbird, and proceed to:
Edit > account settings
it would just shut down thunderbird, no questions asked. Like a crash, without errors.
I figured maybe another system restart was in order, just to get things back on track, but the same thing happened when i pressed my shutdown button. Only my panels disappeared, and i was left at a desktop.

I have no idea why my computer is acting the way it is this morning, and to say it's frustrating is an understatement.
To summarize the problems i'm having, incase someone knows some way of tackling these,
1) Hotmail is not a real domain in thunderbird (I know. I tried using webmail, it worked fine last night, but doesn't this morning)
2) Can not create the temporary file when trying to write an email. (No idea...)
3) No network monitor, doesn't automatically connect to wireless.  Internet is not happy. (Even though I'm sitting on my girlfriend's computer in the same room, and she gets perfect wireless)
4) Shutdown just shuts down panels.  No clue.

These problems seem more like problems that have to be dealt with at the computer, as they're hard to describe to a forum in attempts to get help.  However, if anyone has any idea as to what might be the source of these problems, please let me know.  I'm at the point where I'm almost ready to just reinstall my distro due to this damn thunderbird program.
I really don't think that reinstalling thunderbird would fix this problem, but i suppose anything is worth a try.
Any ideas?

Thanks.

---

### Post by antisocialist on 2007-12-14
instead of using the power button to restart, try pressing ctrl+alt+backspace
it will restart X

---

### Post by llamakc on 2007-12-14
Full disk or partition?

---

### Post by jordank on 2007-12-14
I can restart using the terminal.  I don't want to be banned from using the shutdown button on my computer, that seems kind of silly.
When i say shutdown button, i'm not talking about the physical button on the laptop, but rather the button on my panel that brings up the logoff options.

Ps. I'm using 64bit ubuntu if it makes a difference.

---

### Post by jordank on 2007-12-14
Full disk.

---

### Post by jordank on 2007-12-14
It's funny that you ask that question "Full disk or partition" because after rebooting, i just noticed an error that said
"Low disk space... 100% of disk used" I believe that's what it said, it was only there for a split second.
I'm wondering if maybe Thunderbird filled up what little i had left with emails perhaps? (even though i thought i had way more left?) 

I'm clearing some space off my drive at the moment.
When i open a folder, it says "free space.. 0 bytes"
Is this telling me that i'm at my absolute capacity?

---

### Post by rune0077 on 2007-12-14
Except the first two problems, this does not sound like a Thunderbird problem at all. As for the first Thunderbird problem, the Webmail extension alone is not enough, you'll also need to get the one called Webmail - Hotmail (you need them both). Under the Preferences of the Webmail extension, you also need to be sure that the ports used are actually opened, or change them to someone that are.

Other than that, I can't help you much.

---

### Post by jordank on 2007-12-14
I've done that. I have webmail and hotmail extensions.
I set the ports to ports over 1024, because some operating systems block ports under than number.
I have the ports at 1100 - pop, 1150 stmp, and imap isn't used.
I also have the account settings matching those ports, for my hotmail anyways, so that wasn't the problem.

As for the full disk thing, i just deleted 10 gigs of crap and emptied my trash.  It tells me i have 30 gigs of free space now, so i think it was lying to me earlier.
Unless somehow i had 20 gigs of stuff in my trash, which is unlikely.

I don't think this is a harddrive space issue.

---

### Post by llamakc on 2007-12-14
Ways you can free up a bit of space:

run

```

sudo apt-get autoremove

```The above command will delete the already-downloaded *.deb packages from your cache. This is a safe move if you have internet access.

Before doing anything else, find out WHERE the problem is:

```

sudo du -h --max-depth=1

```The "du" command checks disk usage. The "-h" flag tells it to be human-readable. The "--max-depth=1" flag tells it to only descend the one level.

My output looks like this:

```

ken@llamakc 04:01:15:/$ sudo du -h --max-depth=1
4.0K    ./srv
0       ./proc
112K    ./dev
21M     ./backup
6.4M    ./sbin
4.0K    ./selinux
4.7G    ./usr
0       ./smb
48G     ./home
478M    ./lib
127M    ./opt
4.0K    ./mnt
396K    ./tmp
159G    ./media
4.0K    ./initrd
19M     ./etc
0       ./sys
4.7M    ./bin
67M     ./boot
16K     ./lost+found
1.6G    ./var
83M     ./root
213G    .



```Then, I would compare that with the output of

```

df -h

```Which on my machine looks like:

```

ken@llamakc 04:03:33:/$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              49G  7.2G   39G  16% /
varrun                506M  1.1M  505M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M   68K  506M   1% /proc/bus/usb
udev                  506M   68K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/sda3              98G   48G   45G  52% /home
/dev/hdc1              25G  460M   23G   2% /media/hdc1
/dev/hdc2              50G  5.2G   42G  11% /media/hdc2
//192.168.X.XXX/share   465G  153G  312G  33% /media/Buffalo

```But please, do not go deleting anything from the filesystem until conferring with the forums, and doing some research.

If you do not have a separate /home partition, merely removing some large files or junk from your /home/USER directory can be enough.

---

### Post by jordank on 2007-12-14
Okay, it appears as if everything is fixed (somehow, i didn't do anything..)
with the exception of the logoff button.
When i press the red square on my panel to tell my system to restart, only my panels disappear.  I am typing this with my panels gone, actually, because while i was in the browser i attempted to restart, and now my panels have just disappeared, and i'm left looking at my browser. 
Why is this happening when i press that button? I'm 99 % sure this isn't a disk usage problem.

---

### Post by llamakc on 2007-12-14
Are you using GNOME, KDE, XFCE? Something else?

---

### Post by jordank on 2007-12-15
gnome

---

### Post by llamakc on 2007-12-15
Have you ever mucked with settings in gconf-editor? There's a way to get back to a default setting but it means losing (even if temporarily) any customizations you have made to GNOME.

---

### Post by jordank on 2007-12-18
negative. havent touched them.

---

