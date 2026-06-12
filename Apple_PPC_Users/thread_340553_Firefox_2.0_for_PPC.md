---
title: "Firefox 2.0 for PPC?"
date: 2007-01-17
forum: Apple PPC Users
---

### Post by dpny on 2007-01-17
I have been trying to get the latest Firefox for PPC Ubuntu by looking at [this](https://help.ubuntu.com/community/FirefoxNewVersion) How To. After running into some problems compiling the latest Firefox from source, I noticed the HowTo says:

*Note: Firefox2 is now available in Dapper backports. Please see: [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)*

However, I can't figure out how to get it from the backports. So far as I can tell they are enabled in my sources.list file. So, it seems to be that either 1) Firefox 2 isn't in the PPC backports or 2) I don't know the right **apt-get install** name to ask for. Anyone know if it's one of these two?

---

### Post by nsleiman on 2007-01-17
try this:
sudo apt-get install mozilla-firefox

it should work i guess

---

### Post by dpny on 2007-01-17
> **nsleiman said:**
> try this:
sudo apt-get install mozilla-firefox

it should work i guess

I did that. It tells me that firefox is at the latest version. I also tried any variations I could think of: mozilla-firefox-2, mozilla-firefox-2.0, firefox-2.0, etc.

---

### Post by nsleiman on 2007-01-17
hmm what do you get when typing "firefox" in the konsole ?

---

### Post by dpny on 2007-01-17
> **nsleiman said:**
> hmm what do you get when typing "firefox" in the konsole ?

I can't tell you until I get home from work.

---

### Post by nsleiman on 2007-01-17
download the linux binary from:

[http://www.mozilla.com/en-US/firefox/all.html](http://www.mozilla.com/en-US/firefox/all.html)

unpack and sudo ./firefoxxx.bin

maybe its the binary inside its folder, if its the case unpack it under /opt/ or /usr/bin/

cant remember exactly

---

### Post by dpny on 2007-01-17
> **nsleiman said:**
> download the linux binary from:

[http://www.mozilla.com/en-US/firefox/all.html](http://www.mozilla.com/en-US/firefox/all.html)

unpack and sudo ./firefoxxx.bin

maybe its the binary inside its folder, if its the case unpack it under /opt/ or /usr/bin/

cant remember exactly

I will try it when I get home.

edit: Will this work? That looks like it's an i686 binary.

---

### Post by linear on 2007-01-17
> **dpny said:**
> I will try it when I get home.

edit: Will this work? That looks like it's an i686 binary.

No, it won't work. You are right that it's an i686 binary.

That HowTo in the wiki is out of date. FireFox 2 isn't in Dapper backports. (You can check by searching [here]("http://packages.ubuntu.com/").) I don't know what options you have other than an upgrade to Edgy, unless someone knows of an unofficial repository that has it.

---

### Post by dpny on 2007-01-17
> **linear said:**
> No, it won't work. You are right that it's an i686 binary.

That HowTo in the wiki is out of date. FireFox 2 isn't in Dapper backports. (You can check by searching [here]("http://packages.ubuntu.com/").) I don't know what options you have other than an upgrade to Edgy, unless someone knows of an unofficial repository that has it.

Thanks.

Like I said I'm trying to compile 2.0 from source, but I am running into some errors. I will keep hacking at it. The funny thing is that there's nothing wrong with 1.5. . .

---

### Post by ssam on 2007-01-17
firefox does not get backported because it is used by many other packages. to backport it all those packages would also need to be rebuilt and backported. (though if upstream support of firefox 1.5 stops before ubuntus support of dapper then the ubuntu devs might decide that backporting firefox 2 is easier than maintaining the security of firefox 1.5)

have you read through [http://developer.mozilla.org/en/docs/Build_Documentation](http://developer.mozilla.org/en/docs/Build_Documentation)

you may be missing some build dependencies of firefox try

```
sudo apt-get build-dep firefox
```

if you are still having problems post your error message, and someone can help

---

### Post by dpny on 2007-01-20
> **ssam said:**
> have you read through [http://developer.mozilla.org/en/docs/Build_Documentation](http://developer.mozilla.org/en/docs/Build_Documentation)

I've read it and think I have all the dependencies.

> if you are still having problems post your error message, and someone can help

I keep getting the same error:

```
collect2: ld returned 1 exit status
make[2]: *** [libxpcom_compat.so] Error 1
make[2]: Leaving directory `/opt/src/firefox2/xpcom/obsolete'
make[1]: *** [tier_2] Error 2
make[1]: Leaving directory `/opt/src/firefox2'
make: *** [default] Error 2
```

I googled around and found [this](http://gcc.gnu.org/ml/gcc-bugs/2006-09/msg02205.html) which says trying to build mozilla with GCC 4 or greater fails. I tried to do **make** with

```
export CCVER=gcc33
```

but got the same error.

---

### Post by ssam on 2007-01-21
what does your .mozconfig have in it?

you could try my one from [http://tygier.co.uk/linux/firefox.html](http://tygier.co.uk/linux/firefox.html)

---

### Post by dpny on 2007-01-21
> **ssam said:**
> what does your .mozconfig have in it?

you could try my one from [http://tygier.co.uk/linux/firefox.html](http://tygier.co.uk/linux/firefox.html)

Thanks, man. I will give it a shot later today.

---

### Post by dpny on 2007-01-21
Got the same error. Could it be a problem with the JDK I have installed? I have the free one from synaptic installed. Do I need another one?

---

### Post by ssam on 2007-01-22
building firefox should not require any java.

have you tried redownloading the source. maybe that got corrupted.

---

### Post by dpny on 2007-01-22
> **ssam said:**
> building firefox should not require any java.

have you tried redownloading the source. maybe that got corrupted.

I read something on the Mozilla website which said that building XPCOM requires a JAVA SDK.

---

### Post by ssam on 2007-01-22
> **dpny said:**
> I read something on the Mozilla website which said that building XPCOM requires a JAVA SDK.

i think xpcom is more to do with javascript than java. when i have build firefox from source i've not had any java installed.

---

### Post by dpny on 2007-01-22
> **ssam said:**
> i think xpcom is more to do with javascript than java. when i have build firefox from source i've not had any java installed.

Hmm. . .

Dunno. I will have to mess with it more this week.

---

### Post by dpny on 2007-01-26
I'm still getting the same error.

---

### Post by ssam on 2007-01-27
try one of the mozilla IRC channels, i am sure someone there can help you.

if you are not familiar with IRC have a look at these
[https://wiki.ubuntu.com/IRC](https://wiki.ubuntu.com/IRC)
[https://wiki.ubuntu.com/IRCGuidelines](https://wiki.ubuntu.com/IRCGuidelines)

---

### Post by jctyler1 on 2007-01-27
I admit that I am a newbie to Ubuntu.  Let me see if I understand this thread...The end state is that unless or until I move up to edgy eft, then I am unable to move up to FF 2.0, is that correct?:confused:

---

### Post by patrickfromspain on 2007-01-28
no.. it isn't. Why don't you just get a compiled firefox from [www.getfirefox.com?](www.getfirefox.com?) You just put it where you want and run it from there..

---

### Post by dpny on 2007-01-28
> **patrickfromspain said:**
> no.. it isn't. Why don't you just get a compiled firefox from [www.getfirefox.com?](www.getfirefox.com?) You just put it where you want and run it from there..

Because there is no compiled binary for PPC Linux.

---

