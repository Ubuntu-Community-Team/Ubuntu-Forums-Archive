---
title: "Hi from France and searching for opera"
date: 2005-12-03
forum: Absolute Beginner Talk
---

### Post by dan420 on 2005-12-03
Hello all,
I am quite new to Linux. I have tried almost all the versions of linux for the amd64. I have come back to Ubuntu. I am very much used to opera navigator.
Can any one tell me is there a version for Ubuntu?

---

### Post by Perfect Storm on 2005-12-03
# Opera web browser
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

---

### Post by dan420 on 2005-12-03
Thanks for your reply. I have searched in the forum and did as in some threads.
But I am getting an error msg saying it is not compatible for my amd64 architecture???

do I have to type in the terminal?
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

when I type this in the terminal it says bash: deb: command not found

stuck up!!!

---

### Post by dan420 on 2005-12-03
I have found out that I have to add this line to my apt/sources.list file.
But still I have error message. Unable to localise......
any idea

---

### Post by Terry of Astoria on 2005-12-03
```
# Opera web browser
deb http://deb.opera.com/opera/ etch non-free
```

That looks like an entry to add to your /etc/apt/sources.list
To do that use the command
```
sudo gedit /etc/apt/sources.list
```
then append the line(s) above to the file
then save it.
Then at the terminal try 
```
sudo apt-get install opera
```
--That's my interpretation of the suggestion. I don't use Opera, but I understand they removed the ads for the free version. Cool.

---

### Post by Terry of Astoria on 2005-12-03
Not /apt/sources.list.
/etc/apt/sources.list

---

### Post by dan420 on 2005-12-03
I have the same error message. Unable to localize the list of source package ....

!!!

---

### Post by Terry of Astoria on 2005-12-03
Sorry. Don't forget to 
```
sudo apt-get update
```
after adding sources to sources.list.
Maybe that'll fix your prob.
I was able to add the repository as suggested above
and successfully installed opera only after adding it and after "sudo apt-get update".

---

### Post by dan420 on 2005-12-03
Thanks but even when I do apt-get update i am getting the following error

Impossible to get [http://deb.opera.com/opera/dists/etch/non-free/binary-amd64/Packages.gz](http://deb.opera.com/opera/dists/etch/non-free/binary-amd64/Packages.gz)  404 Not Found [IP*: 193.69.116.19 80]

Impossible to localize the liste of paquets sources [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_etch_non-free_binary-amd64_Packages) - stat (2 Aucun fichier ou répertoire de ce type)

!!!!

---

### Post by Terry of Astoria on 2005-12-03
I don't understand why it didn't work, but how about
[http://opera.com/download/](http://opera.com/download/)
I found I could choose a version for ubuntu.
You would download a *.deb and save it somewhere, and then 
you can install it with 
```
sudo dpkg -i name-of-deb-file
```
from the terminal.

OH! You probably have trouble since you're AMD64, and maybe the deb won't work?

---

### Post by dan420 on 2005-12-03
Tried, geting an error saying that it is not compatible with amd64 architecture

---

### Post by Terry of Astoria on 2005-12-03
see
[http://ubuntuforums.org/showthread.php?t=79618](http://ubuntuforums.org/showthread.php?t=79618)
And, google 
opera ubuntu AMD64
--I found some stuff about how to get flash and stuff to work

---

### Post by dan420 on 2005-12-03
Thanks for your reply, there are some dependency problems.
thanks for your effort

---

### Post by dan420 on 2005-12-04
I have installed the dependencies and then installed opera with the command --force-architecture
It did not give any error message.
But when I execute opera I am getting the following error 

./opera: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory:confused:

---

### Post by lutosdemayo on 2005-12-04
:rolleyes: 

do a force install

something like sudo dpkg -i --force opera*.deb. i have installed opera before on my amd64 but i have switch back to 32 bit

---

### Post by dan420 on 2005-12-04
I have installed the dependencies and then installed opera with the command --force-architecture
It did not give any error message.
But when I execute opera I am getting the following error 

./opera: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

---

### Post by Terry of Astoria on 2005-12-04
Looking in Synaptic for package libqt-mt.so.3 I find that I have installed on mine
the package called libqt3-mt . Do you? Um, but if there are dependencies that package libqt-mt.so.3 needs and aren't present I guess then you might still get that error message even if you do have libqt-mt.so.3. In that case, you'd have to find out the dependencies that are missing somehow . . .

---

