---
title: "Limewire Java error"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by ProjectWhat on 2007-03-21
I tried to install limewire by following this:
[http://www.gnutellaforums.com/showthread.php?t=39850]("http://www.gnutellaforums.com/showthread.php?t=39850")

After I do that I get no errors. It puts the icon in the internet apps menu. But when I click on it it doenst run. So then I go to the terminial and type:
```

limewire
[code]
and I get this:
[CODE]ben@ben-ubuntu:~$ limewire
Starting LimeWire...
Java exec found in PATH. Verifying...
1.4.2-02
OOPS, your java version is too old [java = 1.4.2-02]
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ben@ben-ubuntu:~$ 

```
I have googled and updated java this way:
[https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java")

And I still get the same errors. How would I go about fixing this?:confused:

<edit>
It says that for frostwire also.

---

### Post by charles.g.moore on 2007-03-21
> **ProjectWhat said:**
> I tried to install limewire by following this:
[http://www.gnutellaforums.com/showthread.php?t=39850]("http://www.gnutellaforums.com/showthread.php?t=39850")

After I do that I get no errors. It puts the icon in the internet apps menu. But when I click on it it doenst run. So then I go to the terminial and type:
```

limewire
[code]
and I get this:
[CODE]ben@ben-ubuntu:~$ limewire
Starting LimeWire...
Java exec found in PATH. Verifying...
1.4.2-02
OOPS, your java version is too old [java = 1.4.2-02]
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ben@ben-ubuntu:~$ 

```
I have googled and updated java this way:
[https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java")

And I still get the same errors. How would I go about fixing this?:confused:

maybe you should re-install limewire, it may not know the new java exists

Did you have to do a ./configure, make, make install when you installed limewire?
If so you could do another ./configure and that may fix it

---

### Post by charles.g.moore on 2007-03-21
I use frostwire, it's in the repo's and looks pretty much exactly the same.
Maybe that is an option for you...

---

### Post by ProjectWhat on 2007-03-21
> **charles.g.moore said:**
> maybe you should re-install limewire, it may not know the new java exists

Did you have to do a ./configure, make, make install when you installed limewire?
If so you could do another ./configure and that may fix it

I have uninstalled it using synaptic and reinstalled it. But that didnt work.
As far as the .configure, I dont know what you mean by that. Could you please explain?

---

### Post by charles.g.moore on 2007-03-21
> **ProjectWhat said:**
> I have uninstalled it using synaptic and reinstalled it. But that didnt work.
As far as the .configure, I dont know what you mean by that. Could you please explain?

When you download the source you have to compile it yourself, ./configure is one of the steps in that process.  It's OK if you did not know what it is you probably did'nt build it from source.  Have you looked at Frostwire as an alternative?  Or do you prefer Limewire?  If you want to install Frostwire just to take a look i'll tell you how and if you don't like it you can just un-install it...

---

### Post by ProjectWhat on 2007-03-21
> **charles.g.moore said:**
> When you download the source you have to compile it yourself, ./configure is one of the steps in that process.  It's OK if you did not know what it is you probably did'nt build it from source.  Have you looked at Frostwire as an alternative?  Or do you prefer Limewire?  If you want to install Frostwire just to take a look i'll tell you how and if you don't like it you can just un-install it...

Actually yea frostwire would be great.  I get the same error with frostwire. THe icin is in the apps --> internet menu but it does not launch. 

In the terminial I get this when typing frostwire:
```
ben@ben-ubuntu:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
1.4.2-02
OOPS, your java version is too old [java = 1.4.2-02]
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ben@ben-ubuntu:~$ 

```

So its the same error.

---

### Post by charles.g.moore on 2007-03-21
> **ProjectWhat said:**
> Actually yea frostwire would be great.  I get the same error with frostwire. THe icin is in the apps --> internet menu but it does not launch. 

In the terminial I get this when typing frostwire:
```
ben@ben-ubuntu:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
1.4.2-02
OOPS, your java version is too old [java = 1.4.2-02]
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ben@ben-ubuntu:~$ 

```

So its the same error.

If ound this clip off a website [http://www.google.com/notebook/public/11794900326753401383/BDUU0IgoQk_jDjOkh](http://www.google.com/notebook/public/11794900326753401383/BDUU0IgoQk_jDjOkh)

Common Problems and Work Arounds
Invalid JRE
If you recieve an error such as this 

#
Starting FrostWire...
#
Java exec found in PATH. Verifying...
#
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
#
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
#
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
#
ls: /usr/java/j*: No such file or directory
#
OOPS, unable to locate java exec in  /usr/java/  hierarchy
#
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
#
ls: /opt/j*: No such file or directory
#
OOPS, unable to locate java exec in  /opt/  hierarchy
#
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com) 

Simply type in sudo update-alternatives --config java then select the alternative that includes "sun" in the name. See also Java.

---

### Post by ProjectWhat on 2007-03-21
Awesome, That works for both limewire and Frostwire.
I will probally use frostwire now. I like the way it looks. Is there alot of users using frostwire?

---

### Post by charles.g.moore on 2007-03-21
> **ProjectWhat said:**
> Awesome, That works for both limewire and Frostwire.
I will probally use frostwire now. I like the way it looks. Is there alot of users using frostwire?

Glad I could help, as far as Frostwire goes I have never had a problem grabbing anything.
I'm not too sure about the more obscure stuff (im more of a top 40 kinda listener)

A cool thing to do is bookmark that site I sent you and if you see the same prob. come up share it with others.
The only reason i'm telling you to do it is because i'm on a work puter and cant save it myself

I guess we could just point them to this site...Duh

---

