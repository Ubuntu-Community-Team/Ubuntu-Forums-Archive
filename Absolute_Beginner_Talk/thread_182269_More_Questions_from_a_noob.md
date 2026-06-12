---
title: "More Questions from a noob"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by Ched on 2006-05-25
Alright. So, ive downloaded the G++ compiler...or at least tried to. I downloaded it from Syanptic and I know its on my system, because i can search for the file and it comes up 8 results. My only problem is installing it. I highlight it in Synaptic, hit apply, it downloads and does all of the usual but it dosent install. Hmm...

Any help on this matter would be greatly appriciated. 

Thanks in advance for helping a noob like myself. :)

---

### Post by nalmeth on 2006-05-25
have you installed the build-essential package?
Do you recieve any error?  Or does the package installation freeze, or does it just download and not install? Can you post a screenshot (as attachment) or explain in a little more detail what difficulties you are having?

You can try installing the application through the terminal, if you remember the package name, the command will be:
sudo apt-get install package_name

EDIT:
also, if you can browse to the folder where it is saved (cd /home/username/Desktop for example) you can install the .deb file with:

sudo dpkg -i package_name.deb

---

### Post by Ched on 2006-05-25
It downloads the package, and dosent install. Ive tried sudo dpkg -i package_name.deb, and that didnt work. Let me try getting the build-essential package. Oh, and im not getting an error message. 

Thanks!

---

### Post by nalmeth on 2006-05-25
If there's no error message in the terminal (i.e. it just goes right back to prompt after "setting up package") then it was successfully installed.

---

### Post by Ched on 2006-05-25
But i cant find it/open it... i see the .deb file but i cant find the program on my computer

---

### Post by nalmeth on 2006-05-25
It might just be a command-line tool
In the terminal, type in the first couple letter's of the package and press TAB to let the terminal complete it.
If you find it, to find out how to use it type:
man program

Or look for a project page, possibly on sourceforge or something.

---

