---
title: "AmaroK Wont play MP3's"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by Captain Kirk76 on 2006-08-02
Ive just downloaded AmaroK, but when i add my music to it, it skips them all. I have downloaded and aalready insstalled the MP3 Codec.

---

### Post by Alyus on 2006-08-02
I followed this : (note this wiki has tons of quick answers!!)

[http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Codecs)

to get my mp3's and unprotected aac files to play.  Worked like a charm. I did have to update my sources.list a little bit:

[http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)

I used this site to make a sources.list file that had all kinds of goodies:

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

Good Luck & Enjoy ubuntu!

alyus

---

### Post by orb9220 on 2006-08-02
What version is it that would help. As synaptic only installs 1.3.9 I believe.

To upgrade to 1.4.1  scroll down to kbuntu section and enter those commands in a terminal.


[http://amarok.kde.org/wiki/Installation_HowTo](http://amarok.kde.org/wiki/Installation_HowTo)

---

### Post by Bloch on 2006-08-02
That sounds like what it does when mp3 support is not installed.

Open the terminal. Throw an mp3 file into your home folder (or cd to a directory where there is an mp3 file) and play it with the command
play   __filename__.mp3
Does that work?

---

### Post by Jucato on 2006-08-02
which "mp3 codec" did you install?

for MP3s, you need *libxine-extracodecs* (not w32codecs) which is found in the multiverse repository.

---

### Post by wildseven on 2006-08-02
install easy-ubuntu and install mp3 codecs and other needs through easy-ubuntu. wouldnt that be easier?

---

### Post by Captain Kirk76 on 2006-08-02
Ive installed MP3 Codecs, because Rythm box play them

---

### Post by Jucato on 2006-08-02
But Amarok and Rhythmbox use different engines to play multimedia, so they use different MP3 Codecs. Rhythmbox uses GStreamer, Amarok uses Xine, that's why you need the libxine-extracodecs to make MP3s play in Amarok.

---

### Post by ganceanach on 2007-05-10
OK... I realise that this is a little old and probably more than a little dead but just in case anyone has just installed 7.04 clean and doesn't know how to get mp3's to work and is looking through the forums for how to fix it, here's what worked for me:

sudo aptitude install libxine-extracodecs

Give that a run and see how it goes.

---

