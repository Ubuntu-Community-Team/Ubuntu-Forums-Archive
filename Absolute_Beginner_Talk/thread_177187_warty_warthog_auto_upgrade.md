---
title: "warty warthog auto upgrade"
date: 2006-05-15
forum: Absolute Beginner Talk
---

### Post by scruffy1 on 2006-05-15
i installed ubuntu 4.10 from cd (easily) and was live to the internet, allowing it to install "improvements" made since the cd was sent

it all went swimmingly, but i'd like to know, does 4.10 automagically become 5.10 by doing this

and quite independently, is there a driver for the siemens speedstream 4200 that will let me attach it via usb, so i can keep the ethernet port attached to my other (win xp) computer

yeah, i can use usb to the xp machine if i must, but i'd rather the other way

thx in anticipation

---

### Post by catlett on 2006-05-15
[http://ubuntuforums.org/showthread.php?t=173208](http://ubuntuforums.org/showthread.php?t=173208) This thread has a reply from the ubuntu forum staff saying it is not good to skip a release when upgrading through apt-get.
It appears the best thing is to order a cd from ship it [http://ubuntuforums.org/showthread.php?t=173208](http://ubuntuforums.org/showthread.php?t=173208) after June 1st and do a cd install to Dapper. You'll jump right over Hoary and Breezy.
(or you could download the iso and burn it to a cd and install sooner)

---

### Post by Sef on 2006-05-16
I did a dist-upgrade on my laptop from Warty to Dapper.  I had to go from Warty to Hoary to Breezy to Dapper to do it.  It worked well overall.

---

### Post by catlett on 2006-05-16
[QUOTE=Sef]I did a dist-upgrade on my laptop from Warty to Dapper.  I had to go from Warty to Hoary to Breezy to Dapper to do it.  It worked well overall.[/QUOTE]
Is it as simple as replacing the names in the list? Or if you put stable in will it always dist-upgrade to stable? And if so is it always set up to have servers with "stable" "testing" and the "name" and you can set up your lists either way to get the version (meaning either put the name of the stable version or the word stable)? Or are they distinct server sights with distinct URLs? Just curious about the particulars when dealing with multiple releases and their servers.
Can you always have Hoary if you chose? Or does the server for hoary disappear and become Breezy's server and if you run a dist-upgrade you get the next version. My understanding is that June 1st without changing my repo list I get Dapper packages. Am I wrong?

---

### Post by scruffy1 on 2006-05-16
[QUOTE=catlett][http://ubuntuforums.org/showthread.php?t=173208](http://ubuntuforums.org/showthread.php?t=173208) This thread has a reply from the ubuntu forum staff saying it is not good to skip a release when upgrading through apt-get.
It appears the best thing is to order a cd from ship it [http://ubuntuforums.org/showthread.php?t=173208](http://ubuntuforums.org/showthread.php?t=173208) after June 1st and do a cd install to Dapper. You'll jump right over Hoary and Breezy.
(or you could download the iso and burn it to a cd and install sooner)[/QUOTE]

so, as this is a brand new install and i have nothing to lose except electrons, would i do better to just download the (current) iso and do a complete reinstall

will the cd let me overwrite the current distro, or do i need to reformat the hdd ?

i have oodles of d/l capacity left for the month, and 600meg is a mere hour even without bittorrent.... no waiting till june  :-)

howzat ?

---

### Post by mostwanted on 2006-05-16
[QUOTE=scruffy1]so, as this is a brand new install and i have nothing to lose except electrons, would i do better to just download the (current) iso and do a complete reinstall

will the cd let me overwrite the current distro, or do i need to reformat the hdd ?

i have oodles of d/l capacity left for the month, and 600meg is a mere hour even without bittorrent.... no waiting till june  :-)

howzat ?[/QUOTE]

The CD will let you overwrite the current distro just fine. 

I suggest you download the latest CD as well (the one with Ubuntu 6.06) - it's a major improvement over 4.10, even though it's officially still beta software.

---

### Post by Mr Fat Bat on 2006-05-16
After you upgrade I would suggest heading straight to a "dapper howto" site, there are few around (just google it), one of the better ones is:

[http://easylinux.info/wiki/Ubuntu_dapper]("http://easylinux.info/wiki/Ubuntu_dapper")

---

### Post by Sef on 2006-05-16
> Is it as simple as replacing the names in the list?

I went into the sources list and use the search and replace command.  Saved, then closed gedit.  Next in the terminal, just update, then dist-upgrade.


For those who don't understand the shorthand above:

I opened the terminal (Applications > Accessories > Terminal) and did this to get to my sources list.

1)  sudo gedit /etc/apt/sources.list  

2) Search > Replace  

3) Saved and then closed gedit

(From the terminal)

4) sudo apt-get update

5) sudo apt-get dist-upgrade

Hoary and Breezy were stable.  Dapper is still beta.  

> Can you always have Hoary if you chose?

I can have Hoary on my computer for as long as I want, but after 18 months, it won't be supported.  (about six months from now.)  Not sure how long it will be on the servers.

> My understanding is that June 1st without changing my repo list I get Dapper packages. Am I wrong?

I am not sure if you have to change the repositories or not in your source list.

---

