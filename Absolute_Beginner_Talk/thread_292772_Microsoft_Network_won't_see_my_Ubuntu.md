---
title: "Microsoft Network won't see my Ubuntu"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by ChipMo on 2006-11-04
Hey all, recently loaded up an Ubuntu 5.10 "Breezy Badger" disk onto an old PC, installation went great no problems what so ever. I'm not trying to network the Linux box with my XP pro machine.

I can share my internet connection, both machines can also ping eachother by IP & name (although resolution comes from hosts, not wins / winbind, as that didn't seem to work for me).

Now when I'm on my XP box & I got to network, "MYNET", it's empty, doesn't show "MOFO" (my XP box) or "LinuxBox" (my Linux machine). When I do search computers I can find MOFO & it does say it's in the MYNET workgroup, even though it's not visable on explorer.

When I'm on LinuxBox I check my smbtree I get;
~$smbtree
MYNET
       \\LINUXBOX                          LinuxBox
             \\LINUXBOX\byrnej                   Home Directories
             \\LINUXBOX\ADMIN$                    IPC Service (Samba Server)
             \\LINUXBOX\Share                        
             \\LINUXBOX\print$                    Printer Drivers
~$

Theres two shares, "Share" & byrnej, my home directory, neither fo which I can access on my XP box, and my XP box's share (C:\ drive, share named winxp) doesn't show up on the samba tree, which i think it should?
So I'm pretty sure I have them both on the same workgroup "MYNET" yet they don't see eachother.

I don't know what to do next, I've tried fiddling with everything i can think of, but they still won't see eachother.

I can post a copy of my smb.conf file if that'll be of use, it#s just on default settings atm, but with Workgroup set to MYNET.

cheers if you can help

---

