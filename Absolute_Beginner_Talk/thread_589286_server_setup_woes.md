---
title: "server setup woes"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by CaseyR on 2007-10-24
hello everyone

i recently installed fiesty server edition on a spare computer ive had laying around the house for a while.  my intent (i dont know if it's possible or not) is to have a headless home server that can share/stream music and videos to multiple computers, print serve, and be accessible from outside of my home network when needed.  is this all possible with the same machine?

i've searched around for a few days and havent really come up with anything.  my main problem is that i dont know where to begin.  i installed fiesty with no problems and then fluxbox just in case.  i really like fluxbox btw.  BUT i have no clue how to go about doing any of the things i would like.  im comfortable using the command line as long as someone is guiding me through it.

any info would be great!  im sure there are an abundance of tutorials out there, i guess i just didnt search the right terms.  

thank you

---

### Post by CaseyR on 2007-10-26
could someone at least point me in the right direction?

---

### Post by MegaJim on 2007-10-26
If you want to share printers/folders over a home network using samba, that is relatively easy, just go to system -> administration -> shared folders to set it up

for accessing the stuff outside of the network, you'll probably want to setup an ftp server (not the most secure type of server, but easy to access from outside)

If your box is behind a router you'll need to forward the appropriate ports for access outside the network.  (google port forwarding)

---

