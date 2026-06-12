---
title: "Can A Windows PC on a Network &quot;See&quot; My Ubuntu pc?"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by bme on 2007-07-15
Just a curious question for me. I can connect to our school's LAN and practically do everything allowed on it. It is a Windows network all the instructions on how to connect to it are in windows/IE. I use IE inside Ubuntu to browse the library,etc.
So if I can see the other pc on the computer, can a windows pc see me also? I ask this question because when I am in vista I cannot see the Ubuntu partition in My Computer.

---

### Post by tgm4883 on 2007-07-15
See, kind of subjective.  If you had samba installed, then they would be able to "see" you in Network Neighborhood.

---

### Post by techno-mole on 2007-07-15
it depends on how you have the network set up, i have my ubuntu system networked with 2 other pcs, both of which are running xp, they can see my pc and i can see theres, i can also change, add and delete files and folders on the windows pc's and they can on mine.
cheers

---

### Post by Arisna on 2007-07-15
(Note:  I'm assuming you are using GNOME as your desktop environment)

I think for Windows to be able to "see" your Ubuntu PC, you would need to install the Samba server package, called "samba".  After you install it (use the Synaptic Package Manager), you'll probably have to edit /etc/samba/smb.conf, at least to point your installation to the correct workgroup.  It is likely that other changes will be necessary or desirable for this setup.  Don't worry--the configuration file is well-documented with comments.  After making changes, you have to restart the Samba server.  You can do this without rebooting by entering "sudo /etc/init.d/samba restart".

Once your configuration is in place, you can share files through Nautilus.  As for printers, I'm not sure.  You might be able to do it through the graphical printer configuration tool, but you might have to edit the aforementioned configuration file instead.

---

### Post by techno-mole on 2007-07-15
here is what i do to set up networking.
i go to -->system --> administration --> shared folders, then i select the folder i want to share (note you may get a prompt about installing some files, let it install them) 
once thats done i open terminal and type sudo smpasswd -a and type a password (my user name and password are the same) it will ask you to retype the password.
then in terminal again i type sudo smbpasswd -e username (this enables the user) then i just restart the pc.
when i reboot and go to --> places --> network i can then see the other pc's.
if you run the network setup wizards on the windows pc's it should show your pc on the windows network.
and providing the network is set up ok on the windows pc's you should be able to swap files and such like.
thats all i did to set it up on mine.
cheers
ps - depending on what you want to do, make sure you give the right access to folders, so allow them to be changed by users, otherwise you wont be able to make new files and change others and so on.
as for printer sharing, then yes it is possible, providing you can find drivers that will run the networked printer, i use a lexmark x1270 all in one, and i managed to find a driver that worked for it, and i can print with no problems over the network.

---

### Post by avik on 2007-07-15
There's a great guide [here]("http://ubuntuforums.org/showthread.php?t=103328").  I haven't tried it myself, though.

---

