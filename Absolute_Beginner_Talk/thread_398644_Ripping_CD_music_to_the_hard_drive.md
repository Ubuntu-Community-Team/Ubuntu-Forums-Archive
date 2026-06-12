---
title: "Ripping CD music to the hard drive"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by theninthdimension on 2007-04-01
I have been attempting to rip some music from CDs to my hard drive. I have installed a folder into which I want the music to go and indicated in Sound Juicer where that folder is. However, every time I hit the 'extract' button, I get an error message which reads: [U]Sound Juicer could not extract this CD.
Reason: File not found[/U]. Additionally, whenever I click on the audio disc link in my file browser, I get an error message which reads _"cdda:///dev/scd0" is not a valid location. Please check the spelling and try again_ 

I assume this is some kind of mounting issue. However, the CD will play using Sound Juicer and I have tried the few mounting commands that I know to make sure it is mounted. Any advice or suggestions?

Thanks,

Jeff.

---

### Post by zvacet on 2007-04-02
I don´t see any rreason why play and not extract music.In preferences see is it **strip special characters box** uncheked.Try playing with preferences because I never heard of something like this.I mean program is not complicated and you don´t have many choices in it.That make me think that is something simple.What format do you want to rip?
[https://help.ubuntu.com/community/CDRipping]("https://help.ubuntu.com/community/CDRipping")

---

### Post by theninthdimension on 2007-04-02
Zvacet,

     Thanks for the reply. I have tried ripping from Sound Juicer using every variation of the preferences I could find. I have also tried using different music disk just in case that was the problem. I am still getting the same result.

     I attempted to install RubyRipper, but have had no success getting that installed. I seem to have some sort of retardation that prohibits me from being able to successfully installing tarballs from anywhere.

Thanks,

Jeff.

---

### Post by theninthdimension on 2007-04-02
Update,

     Well, I was able to get RubyRipper to work and the cd did rip. I would still appreciate any guidance on getting Sound Juicer to rip.

Thanks,

Jeff.

---

### Post by Chilli Bob on 2007-04-02
This may be completely off track, but check the permissions on the folder you are trying to put the ripped files into. I got a similar error trying to copy pictures into a file I didn't have permission to access.

---

### Post by theninthdimension on 2007-04-02
ChiliBob,

     Thanks. It was a permissions issue. I had created the folder 'music' in my main file system directory as root and the root permissions were still holding. Changed the permissions and Sound Juicer works like a dream now.

Jeff.

---

