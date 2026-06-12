---
title: "Codec help! UGH"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by 1derphull on 2006-06-02
I have tried EVERYTHING I can think of to get my movies to play.  I used Automatix and added the "NON-FREE" Codecs. 
I used BUMP.  Still, when I click on a movie it just shows a blank screen. 

Video worked with my old install, breezy. Now it doesnt!](*,)

---

### Post by Jimmey on 2006-06-02
What are the extension of the movies? Or are they a DVD?

---

### Post by 1derphull on 2006-06-02
.mov, .mpeg, .wmv  for the most part. 

Forgot to add, I also installed w32codecs.

---

### Post by Jimmey on 2006-06-02
What player are you trying to play these files with?

And you could take a look at [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) ( although this may prove of very little use, as you've already installed the w32codecs ).

---

### Post by 1derphull on 2006-06-02
I'm using totem, but I've also tried VLC. Mplayer doesn't even work (even though it is installed).

---

### Post by 1derphull on 2006-06-02
[QUOTE=Jimmey]What player are you trying to play these files with?

And you could take a look at [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) ( although this may prove of very little use, as you've already installed the w32codecs ).[/QUOTE]

I've seen that, I tried gstraemer0.10-plugins-ugly. 

I get this "Package gstreamer0.10-plugins-ugly is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package gstreamer0.10-plugins-ugly has no installation candidate"

BTW, it says libxine-extracodecs is already up to date

---

### Post by Jimmey on 2006-06-02
I don't know very much about the other two file types, but I'm certain that .wmvs should be playable in Totem with the w32codecs installed.

All I can suggest is that you follow the link that I initally provided, making sure that you stick to the parts relevant to your version of Ubuntu ( Don't use the Dapper guide if you use Breezy, for example ). 

Where you able to play all three of these formats previously?

You might want to try this: 
>  sudo apt-get install totem-xine; sudo apt-get install libxine-extracodecs

Thanks.

---

### Post by 1derphull on 2006-06-02
I can't believe what I'm seeing. I originally edited /etc/apt/sources.list and replaced everything that was "breezy" with "dapper". I saved the changes. 

This is how I upgraded to dapper. Then, when following the "adding repositories howto" in the link you gave me, I saw that it listed Ubuntu 5.10. Then i went back into /etc/apt/sources.list and it reads BREEZY! So, I used gedit and changed it again, then deleted all other instances of sources.list, even the backups. Then I was able to use automatix to upgrade some of the packages that I THOUGHT I upgraded earlier, including the w32 codecs, etc. 

I rebooted, and then looked in my etc/apt/sources.list and it reverted BACK to the old one, with breezy instead of dapper!
The one I thought I saved as sources.list is now 'sources.list'.
I've gone through  this multiple times and it keeps doing the same thing. 

What a headache this is, I had a good thing going with breezy. ](*,) 
I didnt know it'd be this hard to get stuff going.....

---

### Post by LKRaider on 2006-06-02
Are you sure you are using a Dapper compatible Automatix?
Seems to me it is rewriting your sources.list because it is a Breezy version of the script.

---

### Post by 1derphull on 2006-06-03
Just uninstalled automatix, then reinstalled it. My sources.list seems to be ok now. :-D 

Unfortunately it wouldnt let me download the DVD non free codecs, said they "weren't available" whatever that means??

---

