---
title: "Music Downloader for ubuntu"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by bmscwright on 2007-11-20
I want a p2p (gnutella) client NOT LIMEWIRE. for ubuntu that is easy to use. i use bearshare on windows, and i tried running it in wine, and it was unsuccesful. please help and hurry.
step by step is helpful, im kind of new.

---

### Post by Het Irv on 2007-11-20
I have no intent of hijacking this thread but I would also like to know where the best place to get legal music (free or pay).  Along with the answer to the OP question.

---

### Post by Martje_001 on 2007-11-20
Frostwire, no ads:
```
wget http://www.frostwire.com/download/?os=ubuntu
sudo dpkg -i frostwire*.deb
rm frostwire*.deb
```

---

### Post by bobbocanfly on 2007-11-20
gtk-gnutella isnt bad if you really want to use Gnutella. Its in the Repos. 

I really would start downloading music with BitTorrent though.

---

### Post by OffAxis on 2007-11-20
@ Het Irv
 you might be interested in [http://pandora.com/]("http://pandora.com/")
It's an online music repository and player. I've found it to be hit or miss depending on the artist.

You could also try Rhapsody. It's subscription based and $/download, but there's a plugin for firefox that is linux compatible.[http://www.listen.com]("http://www.listen.com")

---

### Post by Het Irv on 2007-11-20
Pandora is good.  And with Firefox and Ad-Block you don't need the subscription.  Great suggestion.

---

### Post by markharding557 on 2007-11-20
emule and its mods run on wine

---

### Post by bluedragon436 on 2007-11-21
Wow...frostwire looks just like limewire, which makes for a very smooth transition if you previously used limewire with MS!!!  Will have to give it a try and see if I get any better luck then I did with Limewire  I would use Rhapsody, or even Pandora....I loved Pandora, but unfortunately I can no longer use Pandora seeing as how I am currently stationed here in Germany and neither one of them are available here in Germany...apparently only available in the U.S. or something ...

---

### Post by al7kz on 2007-11-21
del'td

---

### Post by Ubun2User on 2007-11-24
> **Martje_001 said:**
> Frostwire, no ads:
```
wget http://www.frostwire.com/download/?os=ubuntu
sudo dpkg -i frostwire*.deb
rm frostwire*.deb
```

I did this and I see it in Applications > Internet > Frostwire but when I click it, nothing happens.

Please help.  Thanks!

---

### Post by overdrank on 2007-11-24
> **Ubun2User said:**
> I did this and I see it in Applications > Internet > Frostwire but when I click it, nothing happens.

Please help.  Thanks!

Have you installed the java. And you are on the 64 bit system correct?

---

### Post by kamitsukai on 2007-11-24
> **Ubun2User said:**
> I did this and I see it in Applications > Internet > Frostwire but when I click it, nothing happens.

Please help.  Thanks!
if u have installed java!
u may have to configure your java i think...i had a similar problem ill post back with a link....

---

### Post by smacattack on 2007-11-24
try:

sudo apt-get install   sun-java6-jre

its just the newest version of java that you probably need

---

### Post by Ubun2User on 2007-11-24
Yes I am on 64 bit and no I haven't installed java...newbie here, please tell me how to install Java.

---

### Post by antisocialist on 2007-11-24
in terminal try typing
```
frostwire
```
or if that doesnt work
```
sudo frostwire
```

---

### Post by antisocialist on 2007-11-24
> **Ubun2User said:**
> Yes I am on 64 bit and no I haven't installed java...newbie here, please tell me how to install Java.
go to
apps>add/remove programs

type ubuntu restricted

it will show a package called ubuntu restricted extras.
if u want mp3 wav etc codecs click the checkbox and it will install java along with some music codecs from windoze.

then you can try my above post for getting frostwire to work

---

### Post by Ubun2User on 2007-11-24
Okay did that and I got this in terminal...

Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_03]
Configuring environment...
Loading FrostWire:
Warning: This program is an suid-root program or is being run by the root user.
The full text of the error or warning message cannot be safely formatted
in this environment. You may get a more descriptive message by running the
program as a non-root user or by removing the suid bit on the executable.
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b0458099e25, pid=7586, tid=1076017488
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (1.6.0_03-b05 mixed mode)
# Problematic frame:
# C  [libc.so.6+0x2fe25]  catgets+0x15
#
# An error report file with more information is saved as hs_err_pid7586.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
/usr/lib/frostwire/runFrostwire.sh: line 125:  7586 Aborted                 (core dumped) ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0_03-b05, mixed mode)



Please help!

---

### Post by ExBuM on 2007-11-24
I'm getting this when i try to run frostwire.

```
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_13]
Configuring environment...
Loading FrostWire:

Runtime link error - it appears that libXt got loaded before libXm,
which is not allowed.
java.lang.InternalError: libXt loaded before libXm
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(Unknown Source)
        at java.lang.ClassLoader.loadLibrary(Unknown Source)
        at java.lang.Runtime.loadLibrary0(Unknown Source)
        at java.lang.System.loadLibrary(Unknown Source)
        at sun.font.FontManager$1.run(Unknown Source)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.font.FontManager.<clinit>(Unknown Source)
        at sun.java2d.SunGraphicsEnvironment.addDirFonts(Unknown Source)
        at sun.java2d.SunGraphicsEnvironment.registerFontsInDir(Unknown Source)
        at sun.java2d.SunGraphicsEnvironment.access$200(Unknown Source)
        at sun.java2d.SunGraphicsEnvironment$1.run(Unknown Source)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.java2d.SunGraphicsEnvironment.<init>(Unknown Source)
        at sun.awt.X11GraphicsEnvironment.<init>(Unknown Source)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance(Unknown Source)
        at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(Unknown Source)
        at java.lang.reflect.Constructor.newInstance(Unknown Source)
        at java.lang.Class.newInstance0(Unknown Source)
        at java.lang.Class.newInstance(Unknown Source)
        at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(Unknown Source)
        at sun.awt.motif.MToolkit.<clinit>(Unknown Source)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Unknown Source)
        at java.awt.Toolkit$2.run(Unknown Source)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.awt.Toolkit.getDefaultToolkit(Unknown Source)
        at com.limegroup.gnutella.gui.Main.showInitialSplash(Main.java:67)
        at com.limegroup.gnutella.gui.Main.main(Main.java:39)


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.5.0_13"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_13-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_13-b05, mixed mode)

```

I installed the above Java thing and Ubuntu Restricted thing but still can't get it to work.

---

### Post by rsambuca on 2007-11-24
If you guys are running 64-bit Ubuntu, you need to use the ia32 java for frostwire to work.  You need to open a terminal and run the following:```
sudo apt-get install ia32-sun-java6-bin
```Then run the following to switch to this version```
sudo update-alternatives --config java
```select the ia32 version.

Then Frostwire should work.

Good luck!

---

### Post by Eion on 2007-11-25
I'm having the same problem.

---

### Post by subs on 2007-11-25
my advice would be to use a bittorrent client like azureus...

its damn good... and its pretty useful to download larger files if u are into downloading whole albums at once or perhaps movies and other videos from the net

---

### Post by Kamikaze117 on 2007-11-25
CRAP! HELP!

I entered that thing for the java, it said it was not valid but that another package referenced it. So, I installed  "sun-java6-jre"  and now whenever i try to install anything, even from add/remove, it gives me this:

[COLOR="Red"]E[/COLOR]: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
[COLOR="Red"]E[/COLOR]: _cache->open() failed, please report.

I checked everywhere, but cant find what it means

Remove doesn't work either

Please Help.

Edit: WOW! Weird as hell. After entering  "sudo dpkg --configure -a" 50+ times in terminal it worked and I can use frostwire now. It lets me download things now.

---

### Post by Vivek788 on 2007-11-29
i dont seem to be getting many 192kbps versions of songs with gtk-gnutella as with limewire in windows...can frostwire get me those?
I have downloaded both the 'wires'!!

---

### Post by Presto123 on 2007-12-01
LOL...watch out on that code for frostwire, because they put the "rm" code in it. It removed it when you typed the "rm frostwire" I think. That may just be the .deb package and may not screw with it.

---

### Post by Martje_001 on 2007-12-02
> **Presto123 said:**
> LOL...watch out on that code for frostwire, because they put the "rm" code in it. It removed it when you typed the "rm frostwire" I think. That may just be the .deb package and may not screw with it.
Haha, let me explain the commands ;)

```
wget http://www.frostwire.com/download/?os=ubuntu
```
Retrieve the debian (or ubuntu) package for frostwire.

```
sudo dpkg -i frostwire*.deb
```
Install the debian (or, again, ubuntu) package

```
rm frostwire*.deb
```
Remove the debian (or, again, ubuntu) package to don't leave anything behind.

---

### Post by Presto123 on 2007-12-02
I ran the program without the "rm" command in it with no problems, but I believe what I am getting from this is that it is just for cleaning up. Is that correct?

Thanks for clearing that up...I see "rm" and wonder...

**Edited Addition** Okay...ran the "rm" command with no problems. FYI: At least on my computer, if you are having trouble typing into the text box: disconnect and reconnect and then it runs. It's some odd glitch in my program at least. **

---

