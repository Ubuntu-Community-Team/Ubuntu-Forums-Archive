---
title: "Samba installation problem :s"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by ususim on 2007-12-05
i tried to activate the samba and nfs services thru right-click on folder and select share folder, but when i click on the install services, it seems to not running but keep popping up the same window and eventually the smb and nfs were not installed.

so i tried the sudo command line method and it returned me this message:

[INDENT]xxx@xxx-ubuntu:~$ sudo apt-get install samba
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
ususim@ususim-ubuntu:~$ [/INDENT]

could anybody here help me to solve this problem so that other windows machines can access to the files reside in this ubuntu machine. Thanks!

---

### Post by Znort_Ubern00b on 2007-12-05
its askingt whether or not you have another process open that is stopping apt-get from working. do you have synaptic or update manager open at all???

---

### Post by ususim on 2007-12-05
i need to admit that i am a newbie to linux os.

i am not sure if i had the synatic packager opened because i tried to install the NFS and SMB services when the system tried to retrieve and install the updates, so i first doubt that was the problem, and then i restarted the system.

after the system booted into the desktop, i tried again using the right-click on the folder to share folder method, same thing happened, the same window keeps popping up asking me to click 'install updates'. so i thought that was weird. and i tried to install the samba service in terminal and i got the error quoted in the first thread. i really have no clue about it.

hope that anybody here can guide me thru the process so that my window machines can login to retrieve backup files from the ubuntu machine. 

Thank y'all very much. Cheers...

---

### Post by ususim on 2007-12-05
anybody here to help?

---

### Post by Valnorsith on 2007-12-07
I had a similar problem with installing it and I was told to go to System > Administration > Software Sources and see if the four main boxes under Internet were checked or not. They weren't for me (part of some dumb thing the installer does if there is not an active internet connection while the system is loaded onto the computer). If those boxes aren't checked, then that is most likely the problem since after I checked them, I went to reinstall the two and it worked this time.

Hope this helps you.

---

### Post by jonandrews on 2007-12-07
I've done a step-by-step illustrated guide showing how to network Ubuntu & Windows PC's, biased towards people more familiar with Windows.

[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)

It might help to explain some of your issues...

---

