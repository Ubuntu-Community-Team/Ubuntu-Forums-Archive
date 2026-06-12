---
title: "skype/Alien"
date: 2006-02-08
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2006-02-08
due to an issue with needing libqt3c102-mt i can't install skype. Actually, have it installed but problems running it. I saw a post about someone who resolved this by using alien to install an .rpm version of skype (instead of .deb)

can someone, please tell me how to use alien to do this?

thank you very much

--
sophtpaw

---

### Post by kaamos on 2006-02-08
```
sudo apt-get install alien
```
Download skype rpm from their site
```
sudo alien -i name_of_file.rpm
```

---

### Post by sophtpaw on 2006-02-08
[QUOTE=kaamos]```
sudo apt-get install alien
```
Download skype rpm from their site
```
sudo alien -i name_of_file.rpm
```[/QUOTE]


thank you. i found another thread where it gave the same instructions which i've followed. 
[]("http://www.ubuntuforums.org/showthread.php?p=714996#post714996")

Another question i have however, is whether to first remove the pre-existing version of skype i had installed. 

I don't know whether .rpm version would have simply overwrtitten and replaced the previous version or not. do you (or anyone else) know about this. As it is my skype still doesn't work.

Keep getting dial up failed. and sometimes i've had the error message sound device. ??

I don't know if that is a different problem that neither the .rpm nor .deb version of skype are responsible for or could fix.

all i know skype aint working on my system and i don't know what the real problem is nor what to do. 

Can it be that hard?

Seems to work for some and not for others


--
sophtpaw

---

### Post by lemmy999 on 2006-02-08
tried installing using the method shown on [http://ubuntuguide.org/](http://ubuntuguide.org/), didnt work so used the following (Thanks Kaamos) 


```

Code:

sudo apt-get remove skype --purge 
sudo apt-get install alien 
wget http://www.skype.com/go/getskype-linux-qt32 
sudo alien -i skype-1.2.0.18-suse.i586.rpm 
skype


```

Worked perfectly!!

Suggest that you remove the old version first!

---

### Post by sophtpaw on 2006-02-08
[QUOTE=lemmy999]tried installing using the method shown on [http://ubuntuguide.org/](http://ubuntuguide.org/), didnt work so used the following (Thanks Kaamos) 


```

Code:

sudo apt-get remove skype --purge 
sudo apt-get install alien 
wget http://www.skype.com/go/getskype-linux-qt32 
sudo alien -i skype-1.2.0.18-suse.i586.rpm 
skype


```

Worked perfectly!!

Suggest that you remove the old version first![/QUOTE]

ok, will try removing first.

what is the command exactly please?
 
sudo apt-get remove skype ?
or do you add -purge at the end?

thank you

--
sophtpaw

---

### Post by bartbes on 2006-02-08
as he did add --purge at the end

---

### Post by sophtpaw on 2006-02-08
[QUOTE=bartbes]as he did add --purge at the end[/QUOTE]

with two dashes? "--" this is unusual  that is why i ask, 

thank you for confirming then,

--
sophtpaw

---

### Post by sophtpaw on 2006-02-08
[QUOTE=sophtpaw]with two dashes? "--" this is unusual  that is why i ask, 

thank you for confirming then,

--
sophtpaw[/QUOTE]
 

now i'm getting "segmentation fault" 

when i try and run skype
 
it's not in Applications/Internet/skype and when i try and run it from command line that is the error i get

I followed the instructions to the letter. Removed and purged and installed .rpm with alien

--
sophtpaw

---

