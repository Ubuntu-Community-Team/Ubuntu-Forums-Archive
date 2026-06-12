---
title: "can't connect to ubuntu pc from windows"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by MetalRampage on 2007-09-09
I have recently connected a ubuntu pc to a windows workgroup, samba of course. They are all on the same workgroup. The ubunto pc is finally able to connect and access all network resources, shared folders, printer... I set up a folder to share on my Ubuntu pc. All of my windows workstations recognize that my Ubuntu pc exists, and it seems as though I should be able to access it no problem. Here's the problem though, it asks me for a username and password. I tried all sorts of variations of what I know is the right username and pass that I use to sign in to the Ubuntu workstation, but nothing works.

I am a total noob to linux. If you tell me to put some commands in smb.conf, then tell me how to edit it, I can only open it as a read only document and can't save anything. If you tell me to run some command, please tell me where I type it in.

I've already searched all over the forums, but I just... can't seem to find my way around here.

Many thanks,
MetalRampage

..btw 7.04 fiesty fawn, other systems are winxp and win2k

---

### Post by zachalekos on 2007-09-09
Hello,

Solved the problem.
I did the following:

sudo smbpasswd -a 'myusername'
Add a password when prompted (can be different from pc password).

Then from Windows, simply access shares as usual

When asked for credentials, provide user name, password for samba

---

