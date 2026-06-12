---
title: "album art/ ipod classic/ amarok"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by irishgoth8822 on 2008-02-06
i have an ipod classic that i have just finished syncing with amarok. i have figured out how to right click a song file, hit 'edit information' and 'fetch cover art from amazon.com', but while it saves the cover according to amarok, when i play the music on my ipod, there's no art....what do i need to do?

---

### Post by vinutux on 2008-02-06
thatz bcoz the album arts ur downloaded from amazon is stored in ur local tem folder of amarok......

and amarok not saved this album arts with ur music files .........means ur music files are safe and same as before.........these album arts are only shows when u r playing music from amarock

chck out ur local folder to see ur downloaded album art (/home/[COLOR="Red"]urusername[/COLOR]/.kde/share/apps/amarok/albumcovers)

u need tag editing softwares to editing tags with ur files 

i suggest "easytag" install it edit and add album arts with ur files .......thatz working for ur ipods

---

### Post by TheOrangePeanut on 2008-02-06
I'm not saying the above poster is COMPLETELY wrong because I don't know how Amarok works, but I do know that I can "fetch covers from Amazon" on my Amarok and the album art goes to the Ipod when I transfer the songs.  I'm using an 80g Ipod Classic myself.  How did you go about installing libgpod 0.6.0?

---

### Post by rune0077 on 2008-02-06
> **TheOrangePeanut said:**
> I'm not saying the above poster is COMPLETELY wrong because I don't know how Amarok works, but I do know that I can "fetch covers from Amazon" on my Amarok and the album art goes to the Ipod when I transfer the songs.  I'm using an 80g Ipod Classic myself.  How did you go about installing libgpod 0.6.0?

You'd have to have done that some other way, at some point, because Amarok really doesn't do that, at least not with mp3 files. There is no option to do this, and Amarok stores, as said, the album art locally, it doesn't put it into the tag.

---

### Post by TheOrangePeanut on 2008-02-06
In that case, it may be a Linux Mint thing since I don't run plain Ubuntu.  They might have already configured it to do that.  I also installed libgpod 0.6.0 through a deb and I guess that might have done it too.

---

### Post by irishgoth8822 on 2008-02-06
i installed the libgetc with a deb, using the instructions that somebody in this forum made for configuring linux for an ipod classic. however, like has been said, it will fetch the album cover if i go into the tag edit, but it doesnt show up on the ipod. i presume theres got to be a way to do it, i just dont know how.

---

### Post by rune0077 on 2008-02-07
> **irishgoth8822 said:**
> i installed the libgetc with a deb, using the instructions that somebody in this forum made for configuring linux for an ipod classic. however, like has been said, it will fetch the album cover if i go into the tag edit, but it doesnt show up on the ipod. i presume theres got to be a way to do it, i just dont know how.

There is. As first answer said, download "Easytag". It'll let you edit the tags yourself, but you'll have to do it manually for each song.

---

### Post by vinutux on 2008-02-07
The only two softwares that support album art tag editing music files is "easytag" and "aqualag" player.....i think


anyway givea try these softwares

1.hipo

2.gtkpod



and give atry other music players like

rhythmbox ,listen ,banshee ,exaile....etc

---

### Post by CupofDice on 2008-02-07
There is also albumart-qt at [Softpedia]("http://www.softpedia.com/reviews/linux/Album-Cover-Art-Downloader-Review-49490.shtml"). I think it may embed album art in files because when I am doing album art for my meizu m6 (which recognizes it by the .jpg in the folder, not in the file) some of my files also show album-art. Also when I delete album art the art for the album is deleted, but sometimes the art for the the songs are not even though there is no cover art in the folder.

From Softpedia-

"Other actions include embedding the ID3v2 APIC file into mp3 files."

Can anyone shed any light on this^,

---

