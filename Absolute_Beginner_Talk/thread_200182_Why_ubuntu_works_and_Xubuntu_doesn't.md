---
title: "Why ubuntu works and Xubuntu doesn't?"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by notsowise on 2006-06-19
Hi all. I have been trying to install Xubuntu all afternoon with no success. I have a really old Dell Latitude CPi, Pentium II with only 128mb. After reading the forums I thought Xubuntu would be the better choice. I kept getting an I/O error "buffer overrun on hdc". I have had suprising success installing Kubuntu and ubuntu, they run slow but stable on this old machine. Any suggestions in getting Xubuntu to work?

thx - notsowise:wink:

---

### Post by ProjectGod on 2006-06-19
i guess if it all fails... you could install ubuntu and then download the xfce suite and use it inter-session wise. i'm not too sure about the difference between a clean xubuntu installation and a ubuntu with an xfce or icewm window manger.

---

### Post by Agent86 on 2006-06-19
Where does the install fail? What's the last message you see before the buffer overrun error message?

The Ubuntu and Xubuntu installers are the same AFAIK. You might want to try checking the .iso MD5 checksum and reburning the cd image, perhaps at a slower speed.

You might have to try the alternate install image.

---

### Post by K.Mandla on 2006-06-19
You might try a server installation, then upgrade with *sudo apt-get install xubuntu-desktop*. I'm guessing you have an early hard drive, and that would avoid some of the unnecessary bloat that will come with a straight Ubuntu installation.

(EDITED because what I had written made absolutely no sense whatsoever :roll: )

---

### Post by notsowise on 2006-06-20
Thanks for all of the input. The install fails when I see "Mounting file system". Then I get the buffer overrun. I've downloaded the iso's, (both the Desktop and Alternate) twice with the same error. I've reduced the burn speed to 24x still no luck. I have to check with MD5 checksum so I'll give that a try first. Meanwhile ubuntu is still working fine but slow.....I might just keep it! :rolleyes:

---

### Post by Agent86 on 2006-06-20
[QUOTE=notsowise]Thanks for all of the input. The install fails when I see "Mounting file system". Then I get the buffer overrun. I've downloaded the iso's, (both the Desktop and Alternate) twice with the same error. I've reduced the burn speed to 24x still no luck. I have to check with MD5 checksum so I'll give that a try first. Meanwhile ubuntu is still working fine but slow.....I might just keep it! :rolleyes:[/QUOTE]
This is happening during the initial CD boot? You don't even get to the point of choosing country / keyboard, right?

Check this [thread]("http://www.ubuntuforums.org/showthread.php?t=186115&page=4"), you might need to use the **[FONT="Courier"]ide=nodma[/FONT]** parameter when booting the CD.

If that doesn't work, you can do what K.Mandla says above about the server install (detailed instructions are [here]("https://help.ubuntu.com/community/InstallingXubuntu") or [here]("http://www.psychocats.net/ubuntu/xubuntu").)[FONT="System"][/FONT]

---

