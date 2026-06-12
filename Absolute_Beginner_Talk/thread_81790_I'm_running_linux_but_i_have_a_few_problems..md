---
title: "I'm running linux but i have a few problems."
date: 2005-10-25
forum: Absolute Beginner Talk
---

### Post by brutaldrummer on 2005-10-25
FIrst off let me say that Ubuntu linux rocks, I've played with tons of linux distros and this one is by far the easy user friendly one. Although redhat was pretty friendly but it sure wasn't free. Keep it up!

Here are my problems, my soundblaster live 5.1 card isn't recognized and does not work. 

Next... I have no clue on how to install a program, I opened up synaptic and that's great, but I downloaded a battlefield 1942 server program and it's sitting on my desktop and I have no idea on how to install it. 

Next in my great list is.... From what I understand I can play windows based games using swine or other programs like it. First off, which is the best? I'm a fan of ease, so send me to one that is extremely easy to use.  Second if there is one already on the latest distro where is it? Third... Do I install the cd to the hard drive? how does that work. 

I will probably ask more later, 

Thanks,
TIm:KS

---

### Post by Jenda on 2005-10-25
> Here are my problems, my soundblaster live 5.1 card isn't recognized and does not work. 
No Idea. Go to the HW forum - somebody'll help you there.

> Next... I have no clue on how to install a program, I opened up synaptic and that's great, but I downloaded a battlefield 1942 server program and it's sitting on my desktop and I have no idea on how to install it.
If it's a .deb package, then install it by ```
sudo dpkg -i /full/path/of/your/package.deb
```

> Next in my great list is.... From what I understand I can play windows based games using swine or other programs like it. First off, which is the best? I'm a fan of ease, so send me to one that is extremely easy to use. Second if there is one already on the latest distro where is it? Third... Do I install the cd to the hard drive? how does that work. 
Lol... It's Wine (acronym: Wine Is Not an Emulator). Just install wine and then type ```
wine /full/path/of/the/program/or/installer.exe
```
There is a GUI called xwine. To install both use Synaptic or do: ```
sudo apt-get install wine xwine
```

---

### Post by brutaldrummer on 2005-10-25
i tried to search for wine in synaptic and couldnt find it, but i opened up the terminal anyhow and typed what you showed and it said it couldnt find it or it was obsolete?

---

### Post by Jenda on 2005-10-25
I see. You do not have the extra repos enabled. See here:
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by SilentCacophony on 2005-10-25
> **brutaldrummer]i tried to search for wine in synaptic and couldnt find it, but i opened up the terminal anyhow and typed what you showed and it said it couldnt find it or it was obsolete?[/QUOTE]

It's in the universe repositories. You may want to look at System > Help and look at the *Ubuntu 5.10 Starter Guide*. Here's one way to add the universe repos, quoted from it:

```
How do I add Universe and Multiverse?

    By default, Ubuntu comes pre-configured with basic and security update repositories. To enable the extra Universe and Multiverse repositories:

       1. Start Synaptic by selecting System &#8594 said:**
> Next in my great list is.... From what I understand I can play windows based games using swine or other programs like it. First off, which is the best? I'm a fan of ease, so send me to one that is extremely easy to use.

There is also Cedega from [http://www.transgaming.com/](http://www.transgaming.com/)
I don't think it's free, but I've heard good things about it's useability.

> my soundblaster live 5.1 card isn't recognized and does not work.

Seems like that should work fine. If you're using a live-cd, perhaps it'll handle better upon installaion. Speaking of installation, your last question in the OP, I believe that you have to order or burn an install disc to install it to your HD. I don't think the live-cd can do that (yet.)

---

### Post by kurtkraut on 2005-10-25
Are you sure your sound card is working properly ? I have SoundBlaster Live 5.1 and since Hoary (Ubuntu 5.04) it works fine. It was autodetected with no problems.

---

### Post by brutaldrummer on 2005-10-25
I am not running the live cd I downloaded the ISO for the full installation from the website and then burned it and installed it. I am using the soundblaster live. I'm pretty sure it's the 5.1, I know for a fact it is a soundblaster live tho. It may be older but I don't believe it it.

---

### Post by brutaldrummer on 2005-10-25
Well my sound works now... I turned off my computer took out the sound card to check to see what version it was then put it back in booted into linux and now it recognizes it. That's one less problem out of the way.

---

### Post by brutaldrummer on 2005-10-25
Ok so I download the source to flash player 7...... it's a tar.gz file 

how do i install it?

---

### Post by brutaldrummer on 2005-10-25
So I found the tutorial on how to install codecs in the readme but for some reason the multiverse stuff isn't showing up in my synaptic. The universe stuff is though, any ideas on what may be wrong?

---

### Post by Jenda on 2005-10-25
Well try opening the reopsitory settings in Synaptic and make sure you have Multiverse checked.

---

### Post by brutaldrummer on 2005-10-26
I did that. Everything is checked. I get errors after clicking the multiverse stuff though.

---

### Post by Jenda on 2005-10-26
Please post the error messages, we might be able to figure something out. :wink:

---

### Post by brutaldrummer on 2005-10-26
well right when I just opened synaptic I got

W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)


and then I checked the Multiverse repositories and click apply I get this....

[http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz:) 404 Not Found [IP: 82.211.81.151 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 82.211.81.151 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 82.211.81.151 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 82.211.81.151 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz:) 404 Not Found [IP: 130.239.18.173 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 130.239.18.173 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 130.239.18.173 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 130.239.18.173 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz:) 404 Not Found [IP: 130.239.18.173 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz:) 404 Not Found [IP: 130.239.18.173 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz:) 404 Not Found [IP: 130.239.18.173 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz:) 404 Not Found [IP: 130.239.18.173 80]


and after I click OK this pops up....

W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by Jenda on 2005-10-26
I won't help you with that. You might have to wait for someone who can.

---

### Post by jrw6 on 2005-10-26
Have a look at the repository URL for the "multiverse" entry.  It should be like:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

Whereas you're trying to use backports, which as far as I know doesn't exist any more - hence the error messages ;)

---

### Post by Jenda on 2005-10-26
Ah.. of course. Just don't do the above - all you need is to uncheck the checkbox at "backports". The backports don't exist for Beezy Badger yet.

---

### Post by SilentCacophony on 2005-10-26
If all else fails, you can edit the sources.list file by hand using this page:

[http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

---

### Post by brutaldrummer on 2005-10-27
Now I'm confused... how do I get something out of the multiverse if they are all backports? 

I took a screenshot and marked the multiverse ones I see. Which one do I check to be abel to access the multiverse? I'm pretty confused, because wine or xwine isn't in the universe. 

[http://putfile.com/pic.php?pic=10/29909002624.png&s=x10](http://putfile.com/pic.php?pic=10/29909002624.png&s=x10)

Coming from windows to Linux is pretty confusing.

---

### Post by SilentCacophony on 2005-10-27
Hi. The Synaptic repository settings are a bit difficult to work with in thier current form.

It would probably be easier for you to follow the method outlined in the link I posted above your last post.

If you still want to try it through Synaptic, then make sure that at least the **Ubuntu 5.10 "Breezy Badger" (binary)** entry has universe listed. Also, *uncheck* all entries mentioning backports.

Whichever way you do it, you'll have to then refresh the lists, either through Synaptic or by using the last command on that link.

---

### Post by Jenda on 2005-10-27
Neither of the three. They are backports and those do not work yet. Scroll down and make sure you have the two that say "non-free multiverse" checked. In mine, they are the last two.

---

