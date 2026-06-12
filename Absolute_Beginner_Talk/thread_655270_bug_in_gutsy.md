---
title: "bug in gutsy?"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by loldrup on 2008-01-01
I tried to install flash by following this guide: [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)
(that means, enabling multiverse repository)

Then I went to adobes flash test site, and got this message when I tried to install the Flash plugin:

[[IMG]http://aycu06.webshots.com/image/39245/2003411697589685914_th.jpg[/IMG]](http://allyoucanupload.webshots.com/v/2003411697589685914)

Firefox doesn't seem to be able to see the package. At the same time though, I can see the flash application as being installable when I open the Gnome "Applications" menu and choose "Add/Remove" and search for "Flash"

I also tried installing it via the "Add/Remove"-application, and then entering the flash test site in firefox, but the result is the same.

The computer is a newly installed Ubuntu, and I haven't really done any kind of obscure tweaking that could crack the system.


/Jon

---

### Post by kestrel1 on 2008-01-01
There is a problem with Flash from Ubuntu repository. You need to install using the TAR.GZ file from Adobe:
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
Un-tar the file to a folder on your desktop then go to a terminal window & type:
cd Desktop/Flash_folder (Flash_folder = the name of the folder)
sudo ./flashplayer-installer
That should sort it.

---

### Post by loldrup on 2008-01-01
The installer just laughs at me..

It asks for the path to the mozilla (firefox) browser, and I enter /usr/bin/mozilla/  (after having checked that this directory exists).
It asks me to enter a valid path..
I supply /usr/bin/mozilla/plugins/
no help
I did run it using sudo

It's not any of your guys fault, and I can't (and shouldn't) blame anyone as this is a free OS, but I just got to blow off steam:
I have never experienced a operating system as buggy as Ubuntu (except suse linux 1999). I have now installed it on two computers, one Dell X1 three years old, and one IBM T40p, 4 years old. I have encountered numerous bugs, from freezing to simply not functioning. I can't cope with all these bugs. It's so frustrating and sad. I guess I should just start from an end and report them in the bug tracker, to help improve the <biip>

---

### Post by FuturePilot on 2008-01-01
You need to give it 
```
/usr/lib/firefox
```
as the path

---

### Post by kestrel1 on 2008-01-01
Sorry, I forgot the bit about the folder. FuturePilot is right, that's the folder you need  to point to.

---

### Post by g2g591 on 2008-01-01
Offically supported, easy way to install flash,in a terminal sudo apt-get install flashplugin-nonfree . you can also install it in synaptic, if you want to install java, add sun-java6-plugin to the apt-get command or install it in synaptic too.
EDIT:Oh yeah forgot about that bug, oh well, the java plugin works anyway,

---

### Post by kestrel1 on 2008-01-01
I thought the Gutsy flashplugin-nonfree had a bug? or has this now been sorted. When I tried it, it wouldn't work, so I had to do an install as above.

---

### Post by mcduck on 2008-01-01
The complaint about missing the plugin may just come from the fact that you don't have Shockwave plugin.. That page is testing for both Flash and Shockwave plugins, and it still complains about missing plugin even when you have Flash working. :)

 There is no Shockwave plugin for Linux as Macromedia never made one, and I wouldn't hold my breath waiting for Adobe to do one either..

If you want to install Flash by going to a web site try some site that _only_ needs Flash plugin. Of course you could just install it with Synaptic or the Add/Remove-thing in the Applications-menu.

---

### Post by fparri on 2008-01-01
I also backported Hardy's flashplugin-nonfree to Gutsy. It worked for me
You can find the package here:

[http://rapidshare.com/files/80562619/flashplugin-nonfree_9.0.115.0ubuntu2_7.10prevu1_i386.deb.html](http://rapidshare.com/files/80562619/flashplugin-nonfree_9.0.115.0ubuntu2_7.10prevu1_i386.deb.html)

Hope it helps :)

---

### Post by loldrup on 2008-01-02
> **g2g591 said:**
> Offically supported, easy way to install flash,in a terminal sudo apt-get install flashplugin-nonfree . you can also install it in synaptic, ...


Been there. It didn't work: (see my first post)

---

### Post by loldrup on 2008-01-02
> **mcduck said:**
> 
If you want to install Flash by going to a web site try some site that _only_ needs Flash plugin. Of course you could just install it with Synaptic or the Add/Remove-thing in the Applications-menu.

No, I cannot. That's what the post is all about.

---

### Post by kestrel1 on 2008-01-02
Have you tried downloading from adobe & following my earlier post?

---

### Post by loldrup on 2008-01-04
> **FuturePilot said:**
> You need to give it 
```
/usr/lib/firefox
```
as the path

Hey, It worked - thank you :)

/Jon

---

