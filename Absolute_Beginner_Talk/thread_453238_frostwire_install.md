---
title: "frostwire install"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by Timmy66 on 2007-05-24
can somebody help me install frostwire.I tried to use automatix but I keep getting a apt-based error and it will not install.I know you can use the terminal but do not know exactly how to do it yet,please help.I miss not having a peer to peer.

---

### Post by Terl on 2007-05-24
Why not just go to the frostwire site and download from there?  When the box opens select the choice to install with dpkg and you are set.  Make sure you have java installed.

[Frostwire - pick Ubuntu-Debian]("http://www.frostwire.com/?id=downloads")

---

### Post by DougieFresh4U on 2007-05-24
Why not not just do a google to their web site and download the .deb? Of course you have all your java installed. just a suggestion:p

EDIT:WOW that was quick Terl & almost word for word:p:p

---

### Post by Timmy66 on 2007-05-24
yes I have all the latest java installed.automatix is acting crazy.sometimes it will let me install and sometimes it will not.

---

### Post by Terl on 2007-05-24
> **Timmy66 said:**
> yes I have all the latest java installed.automatix is acting crazy.sometimes it will let me install and sometimes it will not.

Don't use automatix.  Just go to the site, we gave you links, and download direct.  When the download box pops up pick the choice to open with debi package installer.

---

### Post by Timmy66 on 2007-05-24
I did that installed it with debi package manager.it put a icon in apps/internet.when I click on it nothing happens.I'm I just a dumbass or is there something I'm missing.

---

### Post by Terl on 2007-05-24
> **Timmy66 said:**
> I did that installed it with debi package manager.it put a icon in apps/internet.when I click on it nothing happens.I'm I just a dumbass or is there something I'm missing.

Nope, you are not a dumbass; you are learning a new operating system, big difference.  Open a terminal and at the prompt type the word:  frostwire

After you hit enter you should see what is wrong.  Odds are it is something wrong with your java install.  Post what the error is.  Usually the error description is good enough to tell you what to do to fix it.

---

### Post by Timmy66 on 2007-05-24
bloodcrystal@bloodcrystal-1:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)

I tried to update java but I get an error that says method http has died unexpectly.

---

### Post by Terl on 2007-05-24
Using synaptic uninstall (remove) your old java.  

go to:  [Sun Java Site]("https://sdlc1a.sun.com/ECom/EComActionServlet;jsessionid=917E840D0D4FB95525395E3EA8D257ED")

Select the one called Linux self extracting file (4th little check box down).  Accept the license (top left).  Download this to your desktop.  To download, just click the filename, don't bother with the sun download manager.

When the download is done, open a terminal.  Go to the directory where the file downloaded.  Do this command (it is a little L at the end):

```
ls -l
```

For the file you just downloaded you should see a bunch of r's and w's.  At the end ot the rw row there should be an x (last three letters should be like rwx).  If there is no x do this:

```
chmod o+x then the filename
```

For the filename hit the first couple letters and then tab.  It should auto complete the rest of the name.

Check with the ls -l again.  If the x is there do this:

```
sudo sh ./filename
```

It should start installing.

---

