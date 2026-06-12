---
title: "Bootup problems"
date: 2006-02-05
forum: Absolute Beginner Talk
---

### Post by muzcuk on 2006-02-05
Frst of all, I want to share something with you, you can read it or you can skip it and go to the problem. 

I have this new laptop full of non-linux-friendly hardware, and I spent about six hours flat to get it linux to work on it. I had to set up my graphics card manually, I had to mess with acpi stuff because linux doesn't get along well with turion processors, I had to instal ndiswrapper and find 64 bit drivers for my wireless ethernet card and the list goes on. I encountered about 10 million problems during this process but linux always told me what was wrong and there was always someone willing to help at the forums. Most of the time, I didn't even need the forums because there were HOWTO's everywhere. 

Then yesterday evening a friend called me and asked me if I could fix his computer (windows) for him. I spent 8 hours flat to clean the virus/spyware, to get rid of all that fancy stuff that uses all the ram and to update windows so it won't mess itself up again. Plus I couldn't get rid of some of the spyware because windows didn't let me. I'm pretty sure he is gonna call me again next month to do the same thing. Well, I'm getting 20 dollars every time he calls, so its OK with me. 

So, all those people who quit linux because it's so hard to handle, think again...

Now, here is my problem. I finally got ndiswrapper 1.9 to work. But I have some startup problems. It sometimes gets stuck in the start up process. It gets stuck in basically every line that includes the word "network" . Sometimes, it lets me skip it by pressing ctrl+c, in that case, sometimes it gets stuck in "starting hardware abstraction layer", sometimes it doesn't. So, here are the options,

a. starts up flawlessly
b. gets completely stuck in one of the lines with the word "network"
c. gets stuck in network lines, but I can skip it
         1. starts up flawlessly after that point
         2. gets completely stuck in "starting hardware abstraction layer" line
         3. gets stuck in "starting hardware abstraction layer", but I can skip it

if I'm lucky and option a comes into life, everything including wireless works.

if it starts up somehow (c-1 or c-2), wireless doesn't work. but it works after typing "sudo modprobe ndiswrapper" into the terminal.

I read this ([http://www.ubuntuforums.org/showthread.php?t=89491](http://www.ubuntuforums.org/showthread.php?t=89491)) thread and did some modifications in boot-up process but I didn't do any of the "not-sure" modifications, and I left everything about network alone. 

Where should I start checking?

And a bonus question, I figured linux is checking my hardware every time I boot up. I'm using a notebook so my hardware barely changes (I put on a webcam every once in a while). So I want to tell linux, 
"OK, boy, I have this, this and that, you need to load this, this and that and nothing else, so stop all this autodetecting stuff, you're wasting my time. You ain't detecting anything, anyway."
How do I do that? Should I recomplie my kernel for that or can I do that by just modifying some config files.

---

### Post by bscbrit on 2006-02-05
You really need one of the forum's experts to answer this, but I will offer what I can.

Firstly, if your boot-up sequence is having problems then there is something wrong.  If the checks that are taking place during the boot are finding it then it is probably worth trying to find out what it is rather than switching off the checks!  That's a bit like switching off the fire alarm because it goes off everytime something catches fire.  Isn't it supposed to do that?

Can you post the contents of your /etc/network/interfaces file here please?

Also check your boot and system logs (/var/log/dmesg, /var/log/syslog and /var/log/messages) - you will probably find there are plenty of clues to what is going wrong in one or more of them.  They can be pretty big so use 'cat <filename> | less' to look through them.  The error messages tend to be reasonably easy to spot.

---

### Post by muzcuk on 2006-02-05
# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

iface eth0 inet dhcp



iface wlan0 inet dhcp
wireless-essid osman

auto wlan0





Its kinda empty, isn't it?

About the fire alarm, I'm not thinking that as a solution to my problem, I just think the system would be much more solid if it didn't have to worry about hardware changes. It's like building a fireproof building instead of setting up a fire alarm...

---

### Post by muzcuk on 2006-02-05
When I rebooted after my last reply, grub went crazy and deleted windows from the menu, so I fixed it. Then I messed with start up settings again (to restore them to their original settings) and rebooted again, this time when I wrote "sudo modprobe ndiswrapper" , it gave an error.  Then I uninstalled ndiswrapper and recomplied an older version (1.2), it worked. everything is working flawlessly. Not only it boots up normally, but it also connects to the wireless automatically. I don't know what the hell happened, but I got what I wanted. It might be the ndiswrapper version. The problematic one I used was 1.9.

---

