---
title: "Synaptic frozen"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by cliff0108 on 2006-04-17
I had a program fail to install and afterwards receeived error messges from **Synaptic** :

[B]E: Internal error opening cache (1). Please report.
E: Unable to lock the list directory[/B]

I think it's operation is more or less suspended pending resolution of this one install.
Synaptic  help page said this :
[COLOR="Blue"]Synaptic Package Manager requires a clear environment with no 
half installed packages to perform additional changes. But at the moment there is no way to continue canceled installations within Synaptic Package Manager.

To fix this situation type the following command in a terminal, then press Return:
apt-get install -f 
[/COLOR] and I tried this no avail.
I have made many attempted to re-intsall/uninstall the program ( avidemux) all to no avail so far.

Should I try manually deleting all avidemux files ? And more importantly, what can I do to get Synaptic working.?

Anyhelp would be much appreciated.

---

### Post by coolclassic on 2006-04-17
Did you use sudo.

"sudo apt-get install -f"

---

### Post by cliff0108 on 2006-04-17
Thanks CoolClassic - but I get this when I run the suggested command:

cliff@ubuntu:~/downloads$ sudo apt-get install -f avidemux_2.0.24-2_i386.deb
Password:
Reading package lists... Done
Building dependency tree... Done
E: The package avidemux needs to be reinstalled, but I can't find an archive for it.

---

### Post by coolclassic on 2006-04-17
Update your sources by:

sudo apt-get update

Once this has completed then install you package

sudo apt-get install avidemux


don't use version numbers and type of file.

---

### Post by cliff0108 on 2006-04-17
Nope
I ran sudo apt-get update
It updated (apparently)
Then I ran  sudo apt-get install avidemux

and got cliff@ubuntu:~$ sudo apt-get install avidemux
Reading package lists... Done
Building dependency tree... Done
E: The package avidemux needs to be reinstalled, but I can't find an archive for it.


I am trying to manually uninstall and get :
I am having NO END of issues trying to get rideof an application that will neither install nor uninstall and is causing MY SYNAPTIC to freeze. I have received a lot of suggestions about using various apt-get functions to remove/clean/install etc - but a message always returns that the archive cannot be found.
SO I am endeavouring to do the uninstall manually by deleting all references to the file 'avidemux' ( I wish I'd never heard of it!)
However when I do a search in file system I get locations such as :

/home/downloads/opt/gnome/binn avidemux2
/home/downloads/usr/share/doc/packages
/home/downloads/debain etc.


I go to my file browser and I CAN'T EVEN FIND these subdirectories and they do not appear to be hidden? I didn't even know there were apparent subdirectories of the directory 'downloads' which I created !
What is going on?
I am very discouraged and frustrated and no one is able to suggest how to get Synaptic back.

---

### Post by coolclassic on 2006-04-17
You could also use autoclean where in, only those packages in the cache which are found useless or partially complete are deleted.


# apt-get autoclean

then try synaptic if it still fails post the error message

---

### Post by coolclassic on 2006-04-17
After re reading your post i noticed that you are try to install a .deb package from your local drive. To install this type of package you would use the debian package manager "dpkg" in the directory you have saved the file

 sudo dpkg -i avidemux-2.1.2-1_i386.deb

On reading some posts regarding avidmux it seems that there might be some dependancy issues have a look here:

[http://www.ubuntuforums.org/showthread.php?t=78623&page=3](http://www.ubuntuforums.org/showthread.php?t=78623&page=3)

What are you needing this package for there might be something else just as suitable

---

### Post by akak8ty on 2006-09-07
Same. My synaptic package manager has been freezing up all week, and I have to shut down to get out of it.
Very frustrating indeed. The last two times it was hung up on port 80 listening in, the program I was installing didn't seem to much matter.

---

