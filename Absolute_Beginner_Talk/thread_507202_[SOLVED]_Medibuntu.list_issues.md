---
title: "[SOLVED] Medibuntu.list issues"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by jrdba on 2007-07-22
Hello all. I'm new to Ubuntu and was trying to get dvd playability on my new box. After following instructions on help.ubuntu.com, i believe i may have corrupted my sources.list file (what i'm thinking is that I mistyped the letter o instead of capital 'O'). Anytime i try to go to add/remove programs or Synaptic Package manager i get the following error. Please help me restore my sources.list to the original working condition. Thank you.

Error opening the cache E:Type '--15:41:13--' is not known on line 1 in soure list /etc/apt/sources.list.d/medibuntu.list
E:The list of sources could not be read

---

### Post by sad_iq on 2007-07-22
Open a terminal and type ```
gksu gedit /etc/apt/sources.list
``` and correct your mistake :)
 Or try ```
gksu gedit /etc/apt/sources.list.d/medibuntu.list
``` One of these files contains your error!!!

---

### Post by Papi-KB7VGW on 2007-07-22
that is interesting because my sources.list.d is empty!!!!

---

### Post by jrdba on 2007-07-22
I tried the first code, but i can't find my original line that i attempted???

The following is what i'm seeing for the medibuntu.list via 'file system'


--15:41:13--  [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list)
           => `feisty.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 81.169.138.125
Connecting to www.medibuntu.org|81.169.138.125|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 233 [text/plain]

    0K                                                       100%   18.02 MB/s

15:41:15 (18.02 MB/s) - `feisty.list' saved [233/233]

---

### Post by forestpixie on 2007-07-22
post your  /etc/apt/sources.list.d/medibuntu.list

---

### Post by sad_iq on 2007-07-22
> **Papi-KB7VGW said:**
> that is interesting because my sources.list.d is empty!!!!
Mine too but I think that's where medibuntu keeps it's sources.list(or equivalent)!!!
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by forestpixie on 2007-07-22
ok 

```
cd /etc/apt/sources.list.d
```

```
cp medibuntu.list medibuntu.bak
```

```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
```

remove the --15:41:13--

Edit - ```
sudo apt-get update
```

---

### Post by jrdba on 2007-07-22
I followed all your steps (including removing the 15:41:13), but when i try the sudo apt-get update i still get the following....

E: Type 'http://www.medibuntu.org/sources.list.d/feisty.list' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list

---

### Post by forestpixie on 2007-07-22
in terminal 

```
ls /etc/apt/source*
```

and will see what sources.lists you've got

as an aside where did you get the medibuntu repo from?

reason I ask is mine is just sat in sources.list, my /etc/apt/sources.list.d is empty

---

### Post by sad_iq on 2007-07-22
Post your **/etc/apt/sources.list.d/medibuntu.list**...well clean it up!!!!

---

### Post by jrdba on 2007-07-22
here's what lists under that root...

/etc/apt/sources.list  /etc/apt/sources.list~

/etc/apt/sources.list.d:
medibuntu.bak  medibuntu.list  medibuntu.list~

I'm unable to tell you (i forget) where i got the repo from, but I'm certain it was some link within help.ubuntu.com

---

### Post by jrdba on 2007-07-22
what the medibuntu.list looks like right now...

[http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list)
           => `feisty.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 81.169.138.125
Connecting to www.medibuntu.org|81.169.138.125|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 233 [text/plain]

    0K                                                       100%   18.02 MB/s

15:41:15 (18.02 MB/s) - `feisty.list' saved [233/233]

---

### Post by forestpixie on 2007-07-22
will you please post the contents of 


/etc/apt/sources.list.d/medibuntu.list

here for us to see

Edit - or does it actually read


[http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list)
=> `feisty.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 81.169.138.125
Connecting to www.medibuntu.org|81.169.138.125|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 233 [text/plain]

0K 100% 18.02 MB/s

15:41:15 (18.02 MB/s) - `feisty.list' saved [233/233]

---

### Post by jrdba on 2007-07-22
I've done so a couple of times...here it is again below....

[http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list)
           => `feisty.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 81.169.138.125
Connecting to www.medibuntu.org|81.169.138.125|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 233 [text/plain]

    0K                                                       100%   18.02 MB/s

15:41:15 (18.02 MB/s) - `feisty.list' saved [233/233]

---

### Post by forestpixie on 2007-07-22
ok - didn't think that that was actually the file contents 

```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
```

delete the contents of  the file and save 

then do these in terminal 

```
echo "deb http://packages.medibuntu.org/ feisty free non-free" | sudo tee -a /etc/apt/sources.list
```
```

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

that should add the medibuntu repo to your sources list and update it

---

### Post by jrdba on 2007-07-22
Yup exactly...that's basically what's in the medibuntu.list file as of now.

---

### Post by jrdba on 2007-07-22
It worked! thanks so much forestpixie!!!!!!

---

### Post by forestpixie on 2007-07-22
not a problem 6 weeks ago I was sitting in your seat 

can you make sure you edit your first post - go advanced and add solved to the title and there might be a solved button too - helps others out

:D

---

### Post by sad_iq on 2007-07-22
Ok...I have to be a medium to figure this out but I think I got it...you tried to add the medibuntu repo to your sources.list but something went wrong wright??? If I'm not mistaken do this:
 ```
sudo rm /etc/apt/sources.list.d/medibuntu.list
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```
 That should add the correct repos to your sources.list

Edit: Darn...someone outsmarted me :)

---

### Post by forestpixie on 2007-07-22
> **sad_iq said:**
> 

Edit: Darn...someone outsmarted me :)

usually the other way round for me and my slow fingers :)

---

### Post by jrdba on 2007-07-22
Consider it done. thanks again.

---

