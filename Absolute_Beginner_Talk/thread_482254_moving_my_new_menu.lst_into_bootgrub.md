---
title: "moving my new menu.lst into /boot/grub"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by spdpucker on 2007-06-23
I have a dell latitude 131.  I ordered it pre-partitioned at 80/20 on a 160gb hd.  I installed Ubuntu just fine.

here's my problem.  I finally figured out that i have to edit the /boot/grub/menu.lst file.  when I try with the file mgr window it says i don't have permission.  it's owned by root

I then set a root password and then tried to boot as root.  boot menu says I can't boot from there.

so I copied the /boot/grub/menu.lst and saved it in my main folder.  I fixed the default and timeout and saved it.  I can't copy and paste it though.


ok then i opened the terminal window and i'm completely lost now.  i can log in as a su but now what do I do.  I have the file edited and saved as /myron/menu.lst and need to put it in /boot/grub/menu.lst

all i'm trying to do is to set windows as default and give 15 seconds on the bootscreen.

thank you.

**edit**  I really love Ubuntu over fedora.  I been trying a month to set up network printers in fedora on my desktop and Ubuntu set it up on my laptop in 20 seconds.  awsome....

---

### Post by DBStevens on 2007-06-23
mv /myron/menu.1st /boot/grub/menu.1st

Assuming that those are full path names.   The file will no longer exist at /myron/menu.1st as it is moved.

It is probably easier to edit the file directly in /boot/grub/menu.1st by using 

sudo gedit /boot/grub/menu.1st 

in a terminal .

---

### Post by Nythain on 2007-06-23
sudo cp /path/to/menu.lst /boot/grub/menu.lst

extra note, sudo password should be your user password and not the root password, as long as you are still in your sudoers list

---

### Post by spdpucker on 2007-06-23
the dir was actually /home/myron/   I did the mv comand and it worked.  thank you for the help.  I'm used to being spoonfed by msft.  I want more control of my 'puters but I need to learn comand line tactics.  I love this Ubuntu though.  thank you for the help.

---

