---
title: "virtual box and package manager proplems..."
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by baskettplayr on 2007-05-23
here i am with yet another problem.. but thats what you guys are here for so here my prob...
ok i went to install virtual box and it started to install the package like normal and it error and now when ever i want to install something through Synaptic Package Manager this message pops up....

E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

and the archive is right on the desktop i have an original and another one that i downloaded.
??ANy suggestions??

---

### Post by baskettplayr on 2007-05-23
^bump^

---

### Post by bodhi.zazen on 2007-05-23
How did you try to install VirtualBox and what error message did you get ?

An error message about dependencies ?

If so, here is how to install VirtualBox from the CLI:


1. Install dependencies : ```
sudo apt-get install libxalan110 libxerces27
```


2. Install VirtualBox : ```
sudo dpkg -i VirtualBox_1.3.8_Ubuntu_feisty_i386.deb
```

*** Change the version of VirtualBox as needed**


3. If you get dependency errors : ```
sudo apt-get -f install
```



If this does not solve the problem, please provide more information ...

---

### Post by baskettplayr on 2007-05-23
ok i will have to try when i get home...

but right now i will try to explain more

i went to the virtual box website and click the download especially for feisty fawn which is "VirtualBox_1.3.8_Ubuntu_feisty_i386.deb" then i clicked on it and it started to like auto install it or whatever... and then i think the install froze and i turned off the comp and turned it back on and i went to install limewire and the package manager said this "An error occurred... the following details are provided:E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report." then it closes please help.

---

### Post by baskettplayr on 2007-05-23
^bump^

---

### Post by bodhi.zazen on 2007-05-23
So, what happened when you tried to install VirtualBox with the commands I gave you ?

---

### Post by baskettplayr on 2007-05-23
when i entered the first u gave this popped up!: kodey@kodey:~$ sudo apt-get install libxalan110 libxerces27
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
kodey@kodey:~$ 


[IMG]http://i120.photobucket.com/albums/o164/baskettplayr/Screenshot.png[/IMG]

sorry i had the package manager opened still but this is what i got....
[IMG]http://i120.photobucket.com/albums/o164/baskettplayr/Screenshot-kodeykodey.png[/IMG]

---

### Post by bodhi.zazen on 2007-05-23
Did you extract the deb files or some such ? What is is the folder on your desktop "virtualbox .... deb_files"?

More important, where is VirtualBox_1.3.8_Ubuntu_feisty_i386.deb ???

You need to cd to the location of VirtualBox_1.3.8_Ubuntu_feisty_i386.deb

```
cd Desktop/Vitruabox_1.3.8_Ubuntu_feisty_i386.deb_files
sudo dpkg -i VirtualBox_1.3.8_Ubuntu_feisty_i386.deb
```

Assuming the VirtualBox_1.3.8_Ubuntu_feisty_i386.deb is in that folder (or is it on your desktop in which case just 

cd Desktop

---

### Post by baskettplayr on 2007-05-23
k now i got this and this is what is on my desktop



[IMG]http://i120.photobucket.com/albums/o164/baskettplayr/drgsr.png[/IMG]
Any suggestions?

---

### Post by bodhi.zazen on 2007-05-23
OK it looks like the deb package was renamed.

Try this :

```
cd Desktop
mv VirtualBox_1.3.8_Ubuntu_feisty_i386(2).deb VirtualBox_1.3.8_Ubuntu_feisty_i386.deb
```

(or rename the deb package on the desktop by right clicking on it and choosing rename ...

Get rid of the "(2)" so the package is named **VirtualBox_1.3.8_Ubuntu_feisty_i386.deb** )

Then re-install :

```
sudo dpkg -i VirtualBox_1.3.8_Ubuntu_feisty_i386.deb
```

---

### Post by manishk on 2007-05-23
I had exactly the same problem with VirtualBox when I was on Edgy. 

I tried lots of things but nothing worked...and luckily for me it was around April 15th so I just waited for Feisty and did a fresh install.

---

### Post by baskettplayr on 2007-05-24
hey that didnt work either nothing is  i might just have to reinstall it 
hey how do u uninstall ubuntu?

---

### Post by bodhi.zazen on 2007-05-24
If that failed,

Open Synaptic

search for virtualbox

uninstall

Once you uninstall virtualbox your lock error should resolve itself

---

### Post by baskettplayr on 2007-05-24
i cont onpen the manager cause if i do this pops up...

[IMG]http://i120.photobucket.com/albums/o164/baskettplayr/jhtrfg.png[/IMG]

---

### Post by baskettplayr on 2007-05-24
^bump^

---

### Post by bodhi.zazen on 2007-05-24
Damm, why do you have to be so difficult ?

I think the problem is your download was corrupt.

Try this :

```
wget http://www.virtualbox.org/download/1.3.8/VirtualBox_1.3.8_Ubuntu_feisty_i386.deb
md5sum VirtualBox_1.3.8_Ubuntu_feisty_i386.deb
```

md5sum will check the integrity of the download and should be : > 7f493c79a094063d326408dec9b6114a

If the md5sum checks out, then ...

```
sudo dpkg -i VirtualBox_1.3.8_Ubuntu_feisty_i386.deb
```

If not, redownload it.

After Virtualbox is installed you can remove it if you like :)

---

### Post by baskettplayr on 2007-05-24
i will check if it does install im removing this pain in the "***" i mean butt!

---

### Post by baskettplayr on 2007-05-24
one more thing not to be a noob or anything but what do i hit to get past this? i tried clicking ok but that didnt work...
[IMG]http://i120.photobucket.com/albums/o164/baskettplayr/Screenshot-1.png[/IMG]

---

### Post by bodhi.zazen on 2007-05-24
:lolflag:

use the tab key, "OK" will highlight, then use the enter key ...

---

### Post by baskettplayr on 2007-05-24
Yay U Fixed It I Luv U Lol Thanks For Sticking In There With Me!!!!!!!!  Tell Me If U Ever Need To Be Referred About Something Cause I Will!!!

---

