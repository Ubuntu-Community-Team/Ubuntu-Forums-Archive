---
title: "Cant Find ISO File"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by Orangepenguin on 2007-08-30
So, right now I am using Mandriva 2007 and Im hoping to make the switch to Ubuntu shortly.  I downloaded the Ubuntu ISO file from [[COLOR="Blue"]here[/COLOR]]("http://www.ubuntu.com/getubuntu/download") and extracted it to my desktop like i normally do, sifted through the folders looking for it. But, I cant find that damn ISO file:mad:.  Anyone care to point me to where it is or inform me that I am, in fact, an idiot and downloaded the wrong thing?

Thanks.

-orange

---

### Post by mckryptyk on 2007-08-30
type into the command line and wait for it to finish updating its database:

```
sudo updatedb && 
```

then type (you may need sudo here too)

```
slocate *.iso
```

this will search out the iso on you hardrive and show the path to where it is.

Cheers.

---

### Post by phyrewall on 2007-08-30
Why did you extract the ISO? 

Anyway, if you're using FireFox, just go to Tools > Downloads, and you should see the ISO file and be able to figure out where you saved it. From there, just burn the ISO to CD (as an image, not a file).

---

### Post by Orangepenguin on 2007-08-30
> **phyrewall said:**
> Why did you extract the ISO?

I dont know, yeah im using firefox and when it finishes downloading i click open and then pretty much the only option is to extract.
I tried both of your guys suggestions, but neither seems to work for me :(.

EDIT: Nevermind, i found the little ******* hiding in some obscure folder. Thanks :).

---

### Post by mckryptyk on 2007-08-30
Yeah you shouldn't be extracting the ISO. You should be "burning" it to a disk.
And you never said how you downloaded it either.

Cheers.

---

### Post by wormser on 2007-08-30
You might have click open instead of save as when you started your download.  I have done that before.  If that is the case then it should be in your temp directory.  Use the commands posted by mckryptyk to find it.

---

### Post by mckryptyk on 2007-08-30
You can also try this to get it:

In the terminal type:

```
cd /tmp
```

```
ls
```

Once you have found it: (itwill be called whateveritscalled.ISO)

```
cp /tmp/whateveritiscalled.ISO ~/Desktop/mydisk.iso
```

You may have to use sudo in the above command to copy it to the desktop.

If you have to then change it's permissions to your own:

```
cd ~/Desktop
```

```
sudo chown yourusername:yourusername mydisk.iso
```

```
sudo chmod 755 mydisk.iso
```

Cheers.

---

### Post by uilhj on 2007-09-22
> **Orangepenguin said:**
> So, right now I am using Mandriva 2007 and Im hoping to make the switch to Ubuntu shortly.  I downloaded the Ubuntu ISO file from [[COLOR="Blue"]here[/COLOR]]("http://www.ubuntu.com/getubuntu/download") and extracted it to my desktop like i normally do, sifted through the folders looking for it. But, I cant find that damn ISO file:mad:.  Anyone care to point me to where it is or inform me that I am, in fact, an idiot and downloaded the wrong thing?

Thanks.

-orange

I have a similar problem with Orange.

I am using Windows XP, and I installed the download file from the unbuntu website.  After I downloaded it, it came in a .rar file so I extracted all the files.  I cannot find the ISO image in the extracted files.

I looked for this ISO image using search but could not find it.

---

### Post by silverglade00 on 2007-09-22
For some stupid reason, WinRar lets you open an iso file in itself. That is a no-no. You do not ever ever need to extract an iso file. You download it and burn it. There is no need for you to go looking through the folders in the file. Stupid freakin WinRar... I would download the iso again from the Ubuntu site. Save it to the desktop, do not choose run. Then open your CD burning program and follow the directions to Burn a CD Image. I apologize if it seems like I am mad at you. I am not. I am mad at WinRar ever since they started doing this.

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) 
Use that link if you need to loarn how to use an ISO file.

---

### Post by uilhj on 2007-09-23
I just want to point out that silverglade00 is right.

I deleted winrar, and then the downloaded ubuntu file turned into an ISO.

---

