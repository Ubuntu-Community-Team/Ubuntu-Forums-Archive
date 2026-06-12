---
title: "Setting up ninan"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by Alcopops on 2007-02-03
Hi,

I'm very new to linux and ubuntu in particular. I was wondering if anyone can tell me how to get ninan started on edgy. I have installed java common and followed the steps on the ninan web page concerning installation but they are not very detailed. It looks like a good app and I would love to know if any one has got it working so I can compare notes.

Cheers,

Jaime

---

### Post by shareMenaPeace on 2007-02-03
Hi, 
could you post a link to the instructions please?

---

### Post by Alcopops on 2007-02-04
Hi, thanks for the reply, the link to the instructions is here:

[COLOR="Lime"][http://www.ninan.org/modules/mediawiki/index.php/Installation]("http://www.ninan.org/modules/mediawiki/index.php/Installation")[/COLOR]

Because the instructions are so few I have pasted them below

[COLOR="RoyalBlue"]** Installing on a unix machine (mac os x, linux etc)**[/COLOR]

[COLOR="RoyalBlue"]For the unix version the JAVA_HOME has to be correctly pointed to where the java is installed. If you have installed java at /usr/local/java1.5 then this line will do the trick: export JAVA_HOME=/usr/local/java1.5[/COLOR]

>>I couldn't find java 1.5 in the standard repositories (including universe and multiverse etc) but I did find and install java common. This appeared to install to usr/shared/java. so I modified the above line of code and executed it in terminal.

[COLOR="RoyalBlue"]Download the Ninan tar.gz file here[/COLOR]

>>Straight forward.
[COLOR="RoyalBlue"]
Unpack the tar.gz file. This will result in a new directory named like: ninan-x.x.x
[/COLOR]
Yep...
[COLOR="RoyalBlue"]
Go to the new directory run this command: chmod 755 ninancore.sh[/COLOR]

Did this, no errors returned.

[COLOR="RoyalBlue"]Then start Ninan in the background with: nohup ./ninancore.sh & If you do not use the nohup and & then it will not start in the background and the restart feature will not work.[/COLOR]

>>Did this and got some messages that I did not understand but did not appear to be errors. I can try and get the exact responses if it helps.

[COLOR="RoyalBlue"]When you have started ninan this link will get you started if you are on the same machine on which Ninan is installed. [/COLOR]

Unless I'm missing something obvious there is no link here. I'm not sure what to do next. I've used daemons on windows (well just SABNZBd actually)  that require you to point your browser at "local host:specific port" but no address is given here (I tried the address in the windows instructions but got the standard could not load page message in firefox).

Hope this helps you help me.

Cheers again.

Jaime

---

### Post by Lee85il on 2007-10-23
what is the point of using the wiki if the apache server returns an error?

---

### Post by MikeJ112 on 2008-01-23
A bit of a bump!!

I'm having the exact same problem, really not sure where to go from here! Does anybody else use this, or something similar?

Thanks

---

