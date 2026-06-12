---
title: "Installing Programs using the .bin extension"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by AMDarkstone on 2006-08-19
I am currently having a ton of trouble figuring out how to install anything really. codecs, programs... etc. I am new to linux but have used PCs for 10 years. I just bought a book to try and wade myself thru this and it's very very difficult for some reason tho i think it shouldn't be. I hate to bother people's time being a newbie and all, but this is my main issue because it basically makes me wonder what exactly i'm doing wrong or not doing right.

i have a sony vaio laptop that i'm using (where all the hardware drivers aren't installed because i'm still to figure that out) but it runs great. as far as codecs or drivers for popular extensions such as AVI, MP3, and DVD, i've done all that the book says and more and I can't figure out why they're aren't working as well.  

so between those two problems, i have a full plate of wtf this weekend. any help out there?  thanks a whole bunch!


- darkstone

---

### Post by Klaidas on 2006-08-19
For the codecs, see my signature for restricted formats.
For genaral linux lessons, see my signature for linux lessons :)
As for installing, there's a very good howto here: [http://www.psychocats.net/ubuntu/installingsoftware.php](http://www.psychocats.net/ubuntu/installingsoftware.php)

As for installing a .bin file, do
> sudo chmod a+x filename.bin && ./filename.bin

If you have any more questions, just post here :)

---

### Post by AMDarkstone on 2006-08-19
ok, i'm got the bin to execute, now i'm trying to install it into the OPT directory and it says i cannot write to that folder. I am using only one account for ubuntu and it won't let me change the write settings via preferences for the folder.  


should i just install it in a new location, or is this just me getting tooled?


it says it won't let me change the folder settings because i am not the owner?  i am the owner. this kind of stuff gets me boiling because there's only one account, one name, one password... and hence one big problem if i can't even control my own OS.  bah!  lol

---

### Post by Klaidas on 2006-08-19
Hmm, it should allow that as you are using sudo :-k
Which program are you installing? It might be availible in ubuntu packages

---

### Post by AMDarkstone on 2006-08-19
> **Klaidas said:**
> Hmm, it should allow that as you are using sudo :-k
Which program are you installing? It might be availible in ubuntu packages

i am installing planeshift... i'm basically just trying to install Anything. i love running into walls, especially ones as aggrevating as this.


opt folder won't let me change it's settings because for some magical reason i'm 'not the owner'?  which is completely and utterly wrong.

---

### Post by AMDarkstone on 2006-08-19
it doesn't even prompt for a password or anything, so i have no idea how to go about this.

---

### Post by ComplexNumber on 2006-08-19
> **AMDarkstone said:**
> it doesn't even prompt for a password or anything, so i have no idea how to go about this.
once you've typed in sudo <command>, the root privilages stay active for about 4 or 5 minutes (or it may be 10. i can't remember). therefore, it won't ask you for a password if you've already typed in correctly within that time period.
to install stuff, you always need root privilages to install in the usual locations (ie /usr/local and /usr).

all you have to do is go to the command line in the directory where the application you want to instal is, and type:

sudo ./application-name 

where application-name is the exact name of the application. if i'm installing something like solfege.bin, you can use wildcards to save you having to type the whole thing in. so i would do:

sudo ./solf*


let me know how you get on.

btw on EVERY linux system, there are ALWAYS at  least 2 users - the actual user and root(ie administrator). on a single-iuser system, they the user and root are one and the same, but with different permissions.

---

### Post by AMDarkstone on 2006-08-19
so the terminal is basically like using the root.  cause when i double click something to activate an install it thinks i'm not the owner because of ???.  anyways, it worked so far, i'll let you guys know how it goes.


Thanks alot so far, without this i think i would have thrown the install cd at the wall. :)

---

### Post by ComplexNumber on 2006-08-19
> **AMDarkstone said:**
> so the terminal is basically like using the root.  cause when i double click something to activate an install it thinks i'm not the owner because of ???.  anyways, it worked so far, i'll let you guys know how it goes.


Thanks alot so far, without this i think i would have thrown the install cd at the wall. :)
to install ANYTHING in the usual place(ie /usr/local or /usr) where most applications are installed, you need to be root :)
its not like windows where (in most cases) the user is the administrator and can install anything anywhere. thats why viruses and trojans are much more easily installed on windows. trojan writers etc don't need passwords and such like to be able to install nasties on your harddrive. 
thats the reason why you can't login as a root user because malware has the same permissions as the person logged on. if you are running as a user, then the malware only has user permissions. if you are running as root, then the malware has root permissions. therefore, by restricting access in this way, it drastically reduced the ability of malware writers to compromise your system and infect important system files (which users don't have write permissions to).

---

### Post by AMDarkstone on 2006-08-19
so does that mean whenever i have to start the program i have to go into terminal, know the place where the launcher is at, and type sudo before the whole command? or is there a way i can set it up so all i have to do is click the icons they created that are supposed to do that for me?

i have a feeling this is what newbies go thru all the time. this headache because of the mulituser functionality that isn't explained at all well in any book i've read.

---

### Post by Klaidas on 2006-08-19
No, you don't :) (phew!)
Just go to Applications menu, choose a general place where your application could be located (if it's for internet, go to Internet, if it's for drawing/picture editing - go to Graphics) and then click an icon :)

Unless it's a commanline application. Then you should wtite the name of it to use it, like > top.

Also, you don't really need to read lots of books to get started - just see my signature for Linux lessons - they helped me when I was starting linux, it should help you too! :)

---

### Post by AMDarkstone on 2006-08-19
besides all that, the only other issue i have is finding and installing the drivers for my hardware related to my sony vaio laptop.    that's just as much a headache unless synaptic package or wherever makes it easier?

---

### Post by AMDarkstone on 2006-08-19
> **Klaidas said:**
> No, you don't :) (phew!)
Just go to Applications menu, choose a general place where your application could be located (if it's for internet, go to Internet, if it's for drawing/picture editing - go to Graphics) and then click an icon :)

Unless it's a commanline application. Then you should wtite the name of it to use it, like .

Also, you don't really need to read lots of books to get started - just see my signature for Linux lessons - they helped me when I was starting linux, it should help you too! :)

yeah the icons have little 'padlock' icons on them and say i can't do it aka this is what is shown in a warning window:
"**Details: Failed to execute child process "/opt/planeshift/psclient" (Permission denied)**"

---

### Post by equal on 2006-12-07
In case anyone is still reading this thread, I discovered a way of doing it.

```
sudo chmod a+x PlaneShift_CBV0.3.017.bin
```
AND THEN
```
sudo ./PlaneShift_CBV0.3.017.bin
```

Obviously, change the name of the PlaneShift .bin file to the version you downloaded. When I did it how it was originally suggested, I had the same issue as AMDarkstone did . Doing it one line at a time seemed to fix that.

---

