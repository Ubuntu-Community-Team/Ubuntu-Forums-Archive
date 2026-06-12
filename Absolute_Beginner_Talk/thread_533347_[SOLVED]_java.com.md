---
title: "[SOLVED] java.com"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by carloslosgrande on 2007-08-23
[FONT="Comic Sans MS"]Hi, I did a really dumb thing yesterday and broke my system. No trouble, I reinstalled and everything is now hunky dory.
However, in getting frostwire, I discover that I lack java1.5 jre. It's not in the repos (only 1.4) so I tried to get it from java.com (previously automatix took care of this)
I've tried firefox and opera but I just cannot access this site.:confused:
There are a bunch of other sites I'm having the same trouble with, but they lack importance at the moment - to me.
I can get to most of the sites I usually visit.
I'm in China and sometimes sites are blocked, but java?
Anyone else in china got this trouble? Or is it just me?:confused:
Any alternatives?
Thanks.[/FONT]

---

### Post by K.Mandla on 2007-08-23
Try 

```
sudo aptitude install sun-java6-jre
```
That will install from the repositories, which is a stronger solution than relying on Automatix. There's also a *sun-java5-jre*, if you want that.

---

### Post by the.phantom on 2007-08-23
have you enabled all the repositories and looked in synaptic for sun-java6

just click it and the browser plug in

---

### Post by carloslosgrande on 2007-08-24
[FONT="Comic Sans MS"]Hi guys and thanks:)
I already have sun-java5 and 6 jre installed, including the plugins.
All the repos are enabled.
I also have java 1.4 (in the repos), but Frostwire is demanding java 1.5 (not in the repos).
As usual, I have no idea what all these variations of java actually do.:confused:
I'm confused as to why java.com is blocked. I wouldn't have thought their site would warrant such.
Just have to wait a bit I suppose.[/FONT]

---

### Post by the.phantom on 2007-08-24
java 5 is the java 1.5.xx

so might be a frostwire problem?

---

### Post by thatswhatshesaid on 2007-08-24
Sorry to suggest if you already tried this, but have you tried [http://java.sun.com](http://java.sun.com), Java.com looks like a site with games and such.

---

### Post by Seisen on 2007-08-24
Did you do this yet

```
update-java-alternatives -l
``` and select the java 1.5 or 1.6.

---

### Post by carloslosgrande on 2007-08-24
[FONT="Comic Sans MS"]Hi Phantom.
 So java5 is java 1.5 ?? weird.
Ok, maybe its Frostwire, this is what I get from cli;
> ramses@ozymandias:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
1.4.2-02
OOPS, your java version is too old [java = 1.4.2-02]
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
I did have Frostwire working fine prior to the reinstall. I used a 'dpkg' command to re-setup all my apps as they were before the reinstall. Never had ant trouble with this working before.
'Thatswhatshesaid' thanks for the link, I only followed the other as that what is quoted in the error message.
I tried that link but its WAY too complicated for the likes of I. A zillion choices without any directions.
I'm just a simple man.[/FONT]
[FONT="Century Gothic"]I'm considering risking automatix again as I haven't had any trouble with it and does get this stuff done.[/FONT]

---

### Post by igknighted on 2007-08-24
> **carloslosgrande said:**
> [FONT="Comic Sans MS"]Hi Phantom.
 So java5 is java 1.5 ?? weird.
Ok, maybe its Frostwire, this is what I get from cli;

I did have Frostwire working fine prior to the reinstall. I used a 'dpkg' command to re-setup all my apps as they were before the reinstall. Never had ant trouble with this working before.
'Thatswhatshesaid' thanks for the link, I only followed the other as that what is quoted in the error message.
I tried that link but its WAY too complicated for the likes of I. A zillion choices without any directions.
I'm just a simple man.[/FONT]
[FONT="Century Gothic"]I'm considering risking automatix again as I haven't had any trouble with it and does get this stuff done.[/FONT]

Did you install java from java.sun.com?  If so, I would remove it.  It's just harder to set up and enable.  Your best bet it to enable universe/multiverse and install sun-java6* via apt/synaptic.  It should configure everything for you.

...I can't wait for OpenJDK so java isn't an issue anymore...

---

### Post by carloslosgrande on 2007-08-24
[FONT="Comic Sans MS"]Hi Seisen, just saw your post and tried that and I get this;
ramses@ozymandias:~$ update-java-alternatives -1
usage: update-java-alternatives [--jre] [--plugin] [ -t|--test|-v|--verbose]
           -l|--list [<jname>]
           -s|--set <jname>
           -a|--auto
           -h|-?|--help
so obviously I haven't understood your post. Sorry.
Should I put [COLOR="Red"]--jre 1.5[/COLOR] where [COLOR="#ff0000"]-1[/COLOR] is?[/FONT]

---

### Post by igknighted on 2007-08-24
> **carloslosgrande said:**
> [FONT="Comic Sans MS"]Hi Seisen, just saw your post and tried that and I get this;
ramses@ozymandias:~$ update-java-alternatives -1
usage: update-java-alternatives [--jre] [--plugin] [ -t|--test|-v|--verbose]
           -l|--list [<jname>]
           -s|--set <jname>
           -a|--auto
           -h|-?|--help
so obviously I haven't understood your post. Sorry.
Should I put [COLOR="Red"]--jre 1.5[/COLOR] where [COLOR="#ff0000"]-1[/COLOR] is?[/FONT]

thats a lowercase L, not a 1(one).

---

### Post by carloslosgrande on 2007-08-24
[FONT="Comic Sans MS"]Igknighted, thanks. I actually thought that might be l rather than 1 but when I put it in it looked different.
Anyway I get this now;
> ramses@ozymandias:~$ update-java-alternatives -l
java-1.5.0-sun 53 /usr/lib/jvm/java-1.5.0-sun
java-6-sun 63 /usr/lib/jvm/java-6-sun
So I'm to choose one - How?
Or is this showing that I already have this 1.5? If so then Frostwire must be buggered.[/FONT]

[FONT="Comic Sans MS"]I didn't install from anywhere directly, I had my selections saved with this command > dpkg --get-selections ~ grep -v deinstall > ubuntu-files
and after I reinstalled the system I put thes back in with > dselect
So everything was, I guess, downloaded from wherever it came from before, relevant to this is that frostwire was originally loaded via automatix[/FONT]

---

### Post by igknighted on 2007-08-24
Try running it again, but with a "-a" instead of the -l.  If that doesn't set it, use "-s java-6-sun"

---

### Post by carloslosgrande on 2007-08-24
[FONT="Comic Sans MS"][FONT="Comic Sans MS"]Igknighted, brilliant!
That was it exactly. The [COLOR="Red"]-a[/COLOR] option didn't do it but [COLOR="#ff0000"]-s java-6-sun[/COLOR] gave it the kick it needed.
I assume that although I had java 6 installed it wasn't 'set' for use?[/FONT]
Happy days
Thanks man.[/FONT]

---

### Post by igknighted on 2007-08-24
> **carloslosgrande said:**
> [FONT="Comic Sans MS"][FONT="Comic Sans MS"]Igknighted, brilliant!
That was it exactly. The [COLOR="Red"]-a[/COLOR] option didn't do it but [COLOR="#ff0000"]-s java-6-sun[/COLOR] gave it the kick it needed.
I assume that although I had java 6 installed it wasn't 'set' for use?[/FONT]
Happy days
Thanks man.[/FONT]

Exactly.  Since you didn't install the "normal" way (doing the restore), it must have put java back but not switched the config files from gcj to sun java.  Anyways, glad it worked.

---

