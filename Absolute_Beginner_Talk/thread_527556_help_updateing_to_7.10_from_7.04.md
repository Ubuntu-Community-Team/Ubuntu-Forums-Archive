---
title: "help updateing to 7.10 from 7.04"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by darksidedude on 2007-08-16
I tried
update-manager -d

but when I try to update to 7.10 It says on the repositorys Im getting a 404 not found so, is the server down or the updates not working ( I think it could be getting ready for tribe 5) but I'm not shure

---

### Post by kevindubrow on 2007-08-16
I had a similar problem when trying to upgrade from Edgy to 7.04. It turned out that I had not downloaded all of the possible updates. After I updated the computer, I stopped getting error messages and was able to upgrade. I hope this helps!

---

### Post by darksidedude on 2007-08-16
nah man, I did
```
sudo apt-get dist-upgrade
```
and said I was up2date

There is some file on the ubuntu servers that wont transfer:(

---

### Post by diatribe on 2007-08-16
either the server could be down, or you could just change the instances of feisty to gutsy in your sources.lst and see if that helps

---

### Post by Bachstelze on 2007-08-16
First of all, Gutsy is *still in development and might very well break*, think about it twice before upgrading !

If you're really sure you ant to upgrade, you need to change your sources.list from feisty to gutsy, then do an *apt-get update && apt-get dist-upgrade*.

---

### Post by darksidedude on 2007-08-16
so delete the ffiesty part or just add gusty, because I already added the gusty part to the source.list, it shows up in update manager, but A picture would be better so here it is

---

### Post by diatribe on 2007-08-16
anywhere it says 'feisty', just replace it with gutsy.  although I would advise against doing this considering the amount of trouble you are having.  there is a potential for major breakage of your system

---

### Post by isaacj87 on 2007-08-16
I've got a question...

When Gutsy finally comes out, if I upgrade through fiesty (not the liveCD) will it reformat my HDD or just add on top to what i've got.

---

### Post by diatribe on 2007-08-16
it will just upgrade what you have, you will not lose any data

---

### Post by darksidedude on 2007-08-16
ok major breakage dosent matter to me I have a Fedora install as my Main so this is kinda an " experament" because I prefer RPM over Deb so major breakage is fine with me

and to answer your question it wont reformat, it will update ur previous install

---

### Post by darksidedude on 2007-08-16
I figured it out, I had to remove the repository for the commercial porducts ( like vmware server) :lolflag:

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-08-16
is 7.10 out all reddy

---

### Post by diatribe on 2007-08-16
no it is not out yet it will be released in october

---

