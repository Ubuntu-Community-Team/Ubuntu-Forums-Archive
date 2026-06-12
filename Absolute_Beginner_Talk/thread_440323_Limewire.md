---
title: "Limewire"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by rugbydazzla4 on 2007-05-11
Okay, ive got limewire installed and set up my preferences, but now whenever i load it up it has the limewire border etc, but nothign appears in it...

any advice/help?

---

### Post by ghostboy on 2007-05-11
> **rugbydazzla4 said:**
> Okay, ive got limewire installed and set up my preferences, but now whenever i load it up it has the limewire border etc, but nothign appears in it...

any advice/help?

Did you download the Linux version of Limewire or the Windoze version?  If you downloaded the Windoze version and launced the executable file, it may work, but you probably wont see anything like your saying.  Check [http://www.limewire.com]("http://www.limewire.com") to see if they have a Linux version available for download.

---

### Post by rugbydazzla4 on 2007-05-11
i downloaded the linux version

---

### Post by jputman01 on 2007-05-11
have you installed java? either 1.5 or higher?

```
java -version
```

if the answer is no then you will need to install java first, if the answer is yes then my next question is:

are you running beryl or compiz? these programs dont agree with limewire (well frostwire in my experience) if you are running beryl or compiz try disabling beryl/compiz and then running limewire it should start just fine and then you can start beryl/compiz back up. **This is how it works for me anyways**

---

### Post by ashwin_cse on 2007-06-25
> **rugbydazzla4 said:**
> Okay, ive got limewire installed and set up my preferences, but now whenever i load it up it has the limewire border etc, but nothign appears in it...

any advice/help?

I faced similar problem. The solution AFAIK is to switch off the desktop effects. It worked for me atleast.Most probably will work for you too..

HTH

--ashwin

---

### Post by ThrobbingBrain66 on 2007-06-25
Currently there are issues with many Java apps and Beryl/Compiz.  The following link has a very good workaround.  It looks complicated, but if you can copy and paste, you can apply the workaround fairly easily.  I've read that a proper fix is in the works.

[http://wiki.beryl-project.org/wiki/Java](http://wiki.beryl-project.org/wiki/Java)

---

### Post by hyperair on 2007-06-27
I'm using Compiz Fusion from Trevino's eyecandy repository and Java 6 from Feisty's multiverse repository, and Frostwire seems to work fine for me ^^

---

### Post by anemptygun on 2007-09-18
> **jputman01 said:**
> 
are you running beryl or compiz? these programs dont agree with limewire (well frostwire in my experience) if you are running beryl or compiz try disabling beryl/compiz and then running limewire it should start just fine and then you can start beryl/compiz back up. **This is how it works for me anyways**

Why is this? (The link provided by throbingbrain66 is broken)

---

### Post by hyperair on 2007-09-18
Something to do with the GUI toolkit that Swing applications use.. they don't reparent their windows or something like that. The fix:

```
AWT_TOOLKIT="MToolkit"
```

Make sure your /etc/environment file has it. Or just install Compiz Fusion and turn on the Java workaround =P

---

### Post by Baby Boy on 2007-09-18
> **hyperair said:**
> I'm using Compiz Fusion from Trevino's eyecandy repository and Java 6 from Feisty's multiverse repository, and Frostwire seems to work fine for me ^^
Dito, same here. You should try FrostWire, it's just as good without the annoying "Update to LimeWIre Pro now!" messages.

---

### Post by hyperair on 2007-09-18
Before using Frostwire I was using Limewire PRO. Just to let you know. There's a place that supposedly allows you to download it free without license restrictions. [http://limewirepro.at.tt/](http://limewirepro.at.tt/)

---

### Post by Baby Boy on 2007-09-18
> **hyperair said:**
> Before using Frostwire I was using Limewire PRO. Just to let you know. There's a place that supposedly allows you to download it free without license restrictions. [http://limewirepro.at.tt/](http://limewirepro.at.tt/)
How is this possible (legal)?

---

### Post by anemptygun on 2007-09-18
> **hyperair said:**
> Something to do with the GUI toolkit that Swing applications use.. they don't reparent their windows or something like that. The fix:

```
AWT_TOOLKIT="MToolkit"
```

Make sure your /etc/environment file has it. Or just install Compiz Fusion and turn on the Java workaround =P

Thx! i'll try that, and if that wont work... frostwire here i come!:)

---

### Post by anemptygun on 2007-09-18
> **Baby Boy said:**
> How is this possible (legal)?

This was the only thing I could find on their site.

"Limewire is an Open Source P2P Client. The source code is free. You may create the binaries yourself from the GPL licensed sourcecode and distribute them as much as you want, legally."

---

### Post by hyperair on 2007-09-18
That pretty much sums it up =P If you compile it yorself and distribute it, it's legal. If you choose to buy it from them, it's also legal. These people have compiled it themselves and are distributing it. Hence, it is legal.

Anyway you should all just try Frostwire. It's almost identical to Limewire. Works much better than Limewire ever worked for me =P Got this cool community chat too.

---

### Post by anemptygun on 2007-09-18
I can just see the Limewire creators red in the face :P

---

### Post by rfurman24 on 2007-09-18
I do not no if this is relevant after the limwire pro for free post but I was using a limewire Pro rpm converted to deb,using alien, and it was doing the same thing. I just use Frostwire.

---

### Post by hyperair on 2007-09-18
Frostwire > Limewire (Pro)

---

