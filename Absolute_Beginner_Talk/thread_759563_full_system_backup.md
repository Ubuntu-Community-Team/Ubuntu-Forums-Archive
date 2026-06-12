---
title: "full system backup"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by fourthofjuly on 2008-04-19
few days back, i lost my entire Gutsy system to a Mac style menu program that i installed... it did not work but uninstalled most of the relevant packages and i had to make a fresh install... currently Feisty since my Gutsy CD is with a friend...

would like to have an app. that would backup my entire system on my rewritable DVD, including my documents, music, installed apps, packages, themes, even my configuration files... 

so the next time my system crashes, i do a fresh install and simply restore it to the original state it was in before the crash using the DVD backup...

i read about Mondo rescue and Remastersys... there is also one QuickStart script available through these forums... but don't know if theses are the best choices available and if they are open source apps?

for home use, please share if someone has used such tools successfully...

thanks & regards,

devang.

---

### Post by bumanie on 2008-04-19
Not sure about mondo, but the other two you mention are open source as far as I know.  You could also consider drive imaging programs such as:
If hdd space is no problem, gparted will copy a hard drive/partition, but can't compress. There is partimage, clonezilla, ghost4linux and dd commands. Hope this helps.

---

### Post by vinceUUUU on 2008-04-19
Hello

there are many apps that do complete Linux OS  back-ups


There is a free app inside this forum called Quik-Start

Quik-Start can do an entire system backup....into a single file....then you could burn that file to dvd....

quik-start is simple to use...you install it...and select...."create full backup"

then you tick all three boxes..and click go....it takes about 15 minutes...

then you burn the resulting backup file to DVD....

to restore the Linux OS...you select restore from the Quik-start tool and point it to your backed-up file on dvd...

i am not sure what to do if your system has completely crashed and you can not boot into Linux....that would require a rescue CD

there is another free tool on this forum for doing complete backups....it is even more simple than quik-start

called Linubak....i think

Linu something....they are free, search for them in this forum

thanks

Vince.

---

### Post by fourthofjuly on 2008-04-19
> **bumanie said:**
> Not sure about mondo, but the other two you mention are open source as far as I know.  You could also consider drive imaging programs such as:
If hdd space is no problem, gparted will copy a hard drive/partition, but can't compress. There is partimage, clonezilla, ghost4linux and dd commands. Hope this helps.
thanks...

but i just checked out the QuickStart thread, its a good utility & its closed source... 

have you had any experience with any of the tools you mentioned, please?

does Ubuntu have some supported utility for the job? 

thanks

---

### Post by fourthofjuly on 2008-04-19
> **vinceUUUU said:**
> Hello

there are many apps that do complete Linux OS  back-ups


There is a free app inside this forum called Quik-Start

Quik-Start can do an entire system backup....into a single file....then you could burn that file to dvd....

quik-start is simple to use...you install it...and select...."create full backup"

then you tick all three boxes..and click go....it takes about 15 minutes...

then you burn the resulting backup file to DVD....

to restore the Linux OS...you select restore from the Quik-start tool and point it to your backed-up file on dvd...

i am not sure what to do if your system has completely crashed and you can not boot into Linux....that would require a rescue CD

there is another free tool on this forum for doing complete backups....it is even more simple than quik-start

called Linubak....i think

Linu something....they are free, search for them in this forum

thanks

Vince.
thanks...

any open source choices that you could recommend?

---

### Post by george9233 on 2008-04-19
I strongly recommend one called "Home User Backup" (or "HUBackup" in Synaptic), it's very simple to use and can backup straight to a CD or DVD. 

After install it will appear in System->Administration.

---

### Post by fourthofjuly on 2008-04-19
> **george9233 said:**
> I strongly recommend one call "Home User Backup" (or "HUBackup" in Synaptic), it's very simple to use and can backup straight to a CD or DVD. 

After install it will appear in System->Administration.
thanks george, didn't know about that, will check it out for sure... have you tried it out? if so, pl do share your experience...

regards,

devang.

---

### Post by philinux on 2008-04-19
Try remastersys.

[http://www.remastersys.klikit.org/](http://www.remastersys.klikit.org/)

---

### Post by fourthofjuly on 2008-04-19
> **philinux said:**
> Try remastersys.

[http://www.remastersys.klikit.org/](http://www.remastersys.klikit.org/)
pl let me know if you have tried a complete restore with remastersys? kindly share your experience?

thanks & regards,

devang.

---

### Post by philinux on 2008-04-19
My old pc only has a cd rom but my new base unit arriving Tuesday has a dvd burner. I've been dying to try this out ever since I saw it last year.

---

### Post by fourthofjuly on 2008-04-19
> **philinux said:**
> My old pc only has a cd rom but my new base unit arriving Tuesday has a dvd burner. I've been dying to try this out ever since I saw it last year.
ok, any thoughts on Mondo Rescue? 

the website claims its being used by giants like NASA JPL, IBM, Siemens, HP etc... might be very reliable, but don't know until i try it out... 

so i have downloaded and installed it with Synaptic...

anybody out here using it already? pl let me know... i have lost my data once and do not want to take a second chance please...

regards,

devang.

---

### Post by Drakkor on 2008-04-19
Well , I just installed Mondo from the repos,but can't find it in Applications, then I tried the terminal,and it can't find it ! :confused:

---

### Post by fourthofjuly on 2008-04-19
> **Drakkor said:**
> Well , I just installed Mondo from the repos,but can't find it in Applications, then I tried the terminal,and it can't find it ! :confused:
become root and
run mondoarchive in terminal

---

### Post by unutbu on 2008-04-19
```
dpkg --listfiles mondo
```

will tell you where all the files are located associated with the mondo package.

You might also want to install and read the documentation:

```
sudo apt-get install mondo-doc
```

---

### Post by DarkW0lf on 2008-04-19
I have been using sbackup (careful there are two called Simple Backup, I use the GUI one not the shell script) while it makes a compressed copy of the system, the files are huge. Even compressed I have a 10g bz2 archive that takes about a half hour to open if I want to get one file out.

It also makes directories for files it doesn't copy (ie it makes a music directory but I set it not to copy ogg vorbis files and it doesn't).

I like sbackup actually but the large archive takes too long to process.
I needed a backup when I updated to 7.10 but fileroller kept hanging on the 10 or 12g files.

Is there a disk imager that will let me extract one file if I need too ?

---

### Post by Drakkor on 2008-04-19
Thanks, fourthofjuly  , got it !  :)

---

### Post by george9233 on 2008-04-19
Sorry I never tried a full backup, but I did install it and it seems good. 

There's another one called "Simple Backup Config" and "Simple Backup Restore", which is more flexible and full featured, and is also in the repository.

---

### Post by fourthofjuly on 2008-04-20
> **george9233 said:**
> Sorry I never tried a full backup, but I did install it and it seems good. 

There's another one called "Simple Backup Config" and "Simple Backup Restore", which is more flexible and full featured, and is also in the repository.
thanks, but Simple Backup is only for backing up your documents etc. not a full system backup...

i think i will use Mondo for the job since its been  there for quite a number of years... and as it claims to be being used by very big organizations... and its open source...

i guess unless i try it out myself i will never know... 

i will update you all on my experience with Mondo (atleast the backing up part if not system restoration, which is not possible unless my system crashes)

please if someone has had experience with it, kindly share with the community too...

thanks & regards,

devang.

---

### Post by dje on 2008-04-21
> **vinceUUUU said:**
> Hello

there are many apps that do complete Linux OS  back-ups


There is a free app inside this forum called Quik-Start

Quik-Start can do an entire system backup....into a single file....then you could burn that file to dvd....

quik-start is simple to use...you install it...and select...."create full backup"

then you tick all three boxes..and click go....it takes about 15 minutes...

then you burn the resulting backup file to DVD....

to restore the Linux OS...you select restore from the Quik-start tool and point it to your backed-up file on dvd...

i am not sure what to do if your system has completely crashed and you can not boot into Linux....that would require a rescue CD

there is another free tool on this forum for doing complete backups....it is even more simple than quik-start

called Linubak....i think

Linu something....they are free, search for them in this forum

thanks

Vince.

Just to refer to VinceUUUU's post my program called linbaku (always nice to have a compliment :)) is available from the blue link in my signature

dje

---

