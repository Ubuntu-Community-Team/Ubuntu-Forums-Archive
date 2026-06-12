---
title: "help installing open office 2.1"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by deafchickadee on 2007-03-24
I have uninstalled the OO version that came with the Live CD. No problems.

I've installed the latest open office to my desk top....  but im having a little trouble with the code..  

I am following [slga1's]("http://www.ubuntuforums.org/showthread.php?t=318865&page=3&highlight=openoffice+2.1") method. I did this the other day, but had to reformat again. It worked..  but i can't remember how i managed to get it working.

> 1) download OO 2.1 from openoffice.org
2) remove the Ubuntu version of open office -- it's broken anyway
Code:

```
 dpkg -l | grep -i openoffice | cut -d " " -f 3 | sudo xargs apt-get -y --purge remove
sudo apt-get autoremove
```

3) convert the downloaded openoffice files from rpm to deb:
Code:

```
cd dir_where_you_extracted_the_OO_zip_file
cd RPMS
sudo alien --scripts --keep-version *.rpm
```

4) install the new version of openoffice:
Code:

```
sudo dpkg -i *.deb
cd desktop-integration/
sudo dpkg -i *.deb
```

I've installed the  newest version onto my **desktop,** how do i code step 3 with the correct directory... i'm just  little stuck...  


```
cd /home/ella/Desktop/OOo_2.1.0_LinuxIntel_install_wJRE_en-US.tar.gz'
cd RPMS
sudo alien --scripts --keep-version *.rpm
```


Thanks!!!

---

### Post by xopher on 2007-03-24
Hint: OOo 2.2 (beta) is available in Feisty repos ;)

---

### Post by deafchickadee on 2007-03-24
That's not exactly a very unhelpful answer. Sorry :sad: 

I'm not exactly looking to upgrade to fiesty. I want to stick to edgy for now. I've only been using edgy for like a week... and i'm still learning.......


Pleeeeeeease can anyone help me?!?!?!?!?! :oops:

---

### Post by deanjm1963 on 2007-03-24
FIrst you need to have alien installed. Secondly you need to extract the archive which will create folders for you, then you can use the commands to create the deb files from the rpm files and install it.

---

### Post by jvc26 on 2007-03-24
Basically you have to do:
```

sudo apt-get install alien

```
Once that is installed you use cd to change to the directory where the RPM file is located, and execute
```

sudo alien --scripts --keep-version *.rpm

```
Then you can continue the instructions from step 4
Il

---

### Post by deafchickadee on 2007-03-24
Alien is installed..... did that before

ella@ella:~$ sudo apt-get install alien
Reading package lists... Done
Building dependency tree       
Reading state information... Done
alien is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ella@ella:~$ sudo alien --scripts --keep-version *.rpm
File "*.rpm" not found.

RPM file is not found..

Sorry english isn't exactly my first language..

---

### Post by deafchickadee on 2007-03-24
I should also add i extracted onto the desk top

---

### Post by deanjm1963 on 2007-03-24
An easier idea might be to create a folder in your home called rpms.

Copy all the rpms from the archive, and the deb file for menus into that folder.

when in the terminal type

cd rpms

then

sudo alien --scripts --keep-version *.rpm

after it has finished converting

sudo dpkg -i *.deb

---

### Post by deafchickadee on 2007-03-24
okay update.....

Followed your instructions....

looks like it was installed..   but it sounds show on the menu...

how do i find out if it's been installed or not? i accidently closed down the terminal before i could copy and paste what was the last line

---

### Post by deafchickadee on 2007-03-24
oh and FYI...... i can't seem to restart or shut down either...  the quit button won't work

and on thing i forgot to say before.. thankssssss for your help.. i appreciate your help :)

---

### Post by deanjm1963 on 2007-03-24
To fix the log-out problem, just hit Control+Alt+Backpace together, and it should take you back to the login screen.

---

### Post by deafchickadee on 2007-03-24
okay thank you.. that helped...  whew i was worried for one minute....


okay.. how do i find if open office has been installed?

---

### Post by deanjm1963 on 2007-03-24
If its been installed successfully, it should appear in the menu under office.

Did you install the the deb file that was in the desktop-integration folder? Without that, the programs won't appear in the menu.

---

### Post by deafchickadee on 2007-03-24
err..  obviously not? :( 

okay..  can i uninstall and do it again?

how do i uninstall?

---

### Post by deafchickadee on 2007-03-24
by now i must be sounding really dumb....

anyway....  re deb files..  i had a look in the extracted folder..  there isn't any deb files in it but i found a folder called desktop integration folder in the rpm folder you told me to set up...

im like a dog with a bone, i won't budge from my chair until this open office installation is fixed....  i don't want to give up on ubuntu yet...

---

### Post by deanjm1963 on 2007-03-24
the deb file you are looking for is in the desktop-integration folder, just copy that file to your home folder, not into the rpms folder you made, I think its called "debian menus" or something like that and run

sudo dpkg -i *.deb 

and it should install the programs in the menus for you.

There shouldn't be a need to do a complete reinstall. You might need to log out and log in again for the programs to appear in the menu under office.

Hope this helps.

---

### Post by Michaelt74 on 2007-03-24
This is a great tutorial from OSSgeeks, it works well and is straightforward

[http://www.ossgeeks.co.uk/index.php?s=open+office](http://www.ossgeeks.co.uk/index.php?s=open+office)

---

### Post by deafchickadee on 2007-03-24
Thanks Dean!!!!

Thanks Michaell!!

Yay!! it's fixed, up and running!!!

:KS :) =D> 

whew!

---

