---
title: "Making DVDs"
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by James C on 2006-04-01
I've just started using Linux (breezy) and so far i'm finding it good if not a little confusing, as i'm far from being a computer whizz.  

anyway i was wanting to convert some files into DVDs that i can play on my player, I looked at using Varsha which apparently is a graphical interface for making DVDs (it used dvdauthor and the likes in the background), but i can't get it to run.  

can someone give me an idiots guide, what i have done is downloaded the Varsha file from their website, which has put a compressed file on my desktop (similar to a zip file) so i extracted that into a Varsha folder under my Home folder.  it says to run it i need to type  "java -jar varsha.jar" at the command promt (I assume this is the terminal) when i do that i get "bash: java -jar varsha.jar: command not found"  

also the varsha website says i need java 1.5, but i can only find 1.4.  

sorry if this is a stupid question, i hope to get better at ubuntu.

thanks in advance
james

---

### Post by cliff0108 on 2006-04-01
I'm sort of in the same boat - but went to synaptic and installed GnomeBaker and K3b - two separate programs which look promising to burn DVD.
Cliff

---

### Post by taurus on 2006-04-01
[QUOTE=cliff0108]I'm sort of in the same boat - but went to synaptic and installed GnomeBaker and K3b - two separate programs which look promising to burn DVD.
Cliff[/QUOTE]
You still have to convert your movie files to a DVD format before you can burn them wth k3b!  

The question is did you install java on your system???

---

### Post by James C on 2006-04-01
i have java 1.4, which is the only version available via synaptic

---

### Post by taurus on 2006-04-01
[QUOTE=James C]i have java 1.4, which is the only version available via synaptic[/QUOTE]
Then why don't you use synaptic to remove it.  Then head over to Sun's, [url]
http://java.sun.com/[/url] and download the latest version, 1.5, then...  [https://sdlc4d.sun.com/ECom/EComActionServlet;jsessionid=FEEA46E560E36DEA8F4AA06AF5F1C5AC](https://sdlc4d.sun.com/ECom/EComActionServlet;jsessionid=FEEA46E560E36DEA8F4AA06AF5F1C5AC).  Download the jdk-1_5_0_06-linux-i586.bin version and move it to /opt using sudo.  Then, change permission and unpack to install it...
```

sudo mv jdk-1_5_0_06-linux-i586.bin /opt
chmod 755 jdk-1_5_0_06-linux-i586.bin
./jdk-1_5_0_06-linux-i586.bin

```
Then, your latest version of java should be in /opt/jdk1.5.0.06/bin/java or something close to that name...

---

### Post by James C on 2006-04-01
cheers i'll try that

---

### Post by taurus on 2006-04-01
Don't forget to either link it or put it in your path so programs can find your latest version of java or run
```

sudo alternatives --config java

```

---

### Post by Mustard on 2006-04-01
There is another documented method for installing Sun Java at the wiki too.

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

