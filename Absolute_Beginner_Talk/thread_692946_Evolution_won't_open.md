---
title: "Evolution won't open"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by chrisk50 on 2008-02-10
Hi - First request so I hope I'm doing it right. I was running 7.04 Ubuntu and tried to dual boot it with PCLOS but Grub did not recognise Ubuntu. I didn't know how to edit Grub and didn't fancy PCLOS so I did a fresh install of 7.10 using a disk from Linux Format with the enhanced version. Xfce didn't work properly neither would Evolution open. As I had previously had problems loading MMCodecs into Edubuntu 7.10 I decided just to go back to 7.04 and formatted slave hdb to single partition ext3. (hda has /,/home and swap partitions). Reformatted hda1 as / and did fresh install. Still Evolution didn't open. Firstly I used Synaptic to re-install EVO to no effect, then I came to this forum and started working through the posts.
a:sudo killall -r evolution* No Result
b:sudo killall -r gnome-keyring* No Result
c: $ cd /usr/lib/evolution/2.10/plugins
   $ mv org-gnome-sa-junk-plugin.eplug{,-disabled} No Result.
Out of desperation I have just done another fresh install after removing evolution.backup from my Home folder and still Zilch.
I can access my mail and diary by dropping the .evolution folder into an old laptop running Edubuntu but I really need to get this back up and running on my D'top as I run a social project from it. URGENT HELP (Pretty Please).
(I'm running AMD 2000XP on K7mobo, 512RAM, SB128, Nvidia 128 dual head graphics but using Ubuntu drivers.) cheers, Chrisk

---

### Post by linuxmagick on 2008-02-14
Do you get any additional output, such as an error message, when trying to launch Evolution from a terminal?  If so, please provide me with that information so I can accurately respond to the issue you are experiencing.

---

### Post by dcstar on 2008-02-14
> **chrisk50 said:**
> Hi - First request so I hope I'm doing it right. I was running 7.04 Ubuntu and tried to dual boot it with PCLOS but Grub did not recognise Ubuntu. I didn't know how to edit Grub and didn't fancy PCLOS so I did a fresh install of 7.10 using a disk from Linux Format with the enhanced version. Xfce didn't work properly neither would Evolution open. As I had previously had problems loading MMCodecs into Edubuntu 7.10 I decided just to go back to 7.04 and formatted slave hdb to single partition ext3. (hda has /,/home and swap partitions). Reformatted hda1 as / and did fresh install. Still Evolution didn't open. 
..........

Running different distros/versions on the same /home partition can change things that stop apps working when you try to use other versions again.

Rename your (hidden) .evolution folder, restart Evolution and you should have a fresh (empty) system.

Shut down Evolution and then manually copy the various data files from the renamed directory to the new .evolution directory - you should (eventually) be able to recover your data.

---

