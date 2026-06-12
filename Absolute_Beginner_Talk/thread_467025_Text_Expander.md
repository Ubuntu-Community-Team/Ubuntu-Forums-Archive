---
title: "Text Expander?"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by tylercarbone on 2007-06-07
I'm new to Linux, and just sorting out a switch from OSX. For the most part this has gone fairly well, and I've found programs for everything that I want to do... except for a text expander, like Textpander or Typinator. Does such a thing exist for Linux? Google returns nothing, and the occasional forum post elsewhere seems to indicate that it doesn't, but I figured I'd put it to you all here.

Thanks in advance,
Tyler

---

### Post by tylercarbone on 2007-06-08
In case anyone else is interested, it looks like there *is* in fact a text expander for Linux, in the form of 'kbd-mangler' ([http://kbd-mangler.sourceforge.net/](http://kbd-mangler.sourceforge.net/)). I haven't tried it yet, but it at least ostensibly does what I and others need.

---

### Post by peabody on 2008-02-18
Sorry to resurrect this old thread, but I'm currently plugging my project autokey which should be able to do just what you need.  The link to the sourceforge page is in my signature.  If you could give it a try and let me know if it works for you, that would be great.

---

### Post by adpads on 2008-02-20
YES! You guys ROCK!

I'm a translator by trade, and was forced to abandon my last attempt to migrate to Linux about two and a half years ago due to my idiotic need for As-U-Type Speller, a dorky little piece of Windows garbage spewed out by some monolongual Australian for profit.

Now I am so excited to see that someone has even attempted to save civilization for myself and the half-dozen desperate Linux-curious medical transcriptionists out there whom all my hundreds of hours of Google-scouring have uncovered, that I will go out on a limb and thank you now, in advance of even trying out the software.

And of course, after I have done so, I will come back and leave a couple of pennies' worth for the transcriptionists of the future, and for the programmers who have saved our lives and livelihoods, and I will also possibly promise you my firstborn, etc. etc.

Yours at last,
adpads

---

### Post by timcredible on 2008-02-20
looks like openoffice can do this:  link [here]("http://lifehacker.com/software/feature/save-time-with-text-substitution-162484.php").

---

### Post by adpads on 2008-02-21
OpenOffice can do it, but this is a great solution for those who have to type into other applications.

I installed version 0.30 from the .deb (as per instructions in your other thread, [http://ubuntuforums.org/showthread.php?t=679612&page=7](http://ubuntuforums.org/showthread.php?t=679612&page=7)).. tried installing from the tarball, but this is what I got:

cp hotstring_logger *.py /usr/local/bin
cp: cannot stat `hotstring_logger': No such file or directory
make: *** [install] Error 1

I'd say in the next revision maybe the talking voice should be off by default. Is there a way to turn it off?
I'll come back and try the next one - I'm glad to see a solution is very close..

---

### Post by peabody on 2008-02-21
> **adpads said:**
> 
cp hotstring_logger *.py /usr/local/bin
cp: cannot stat `hotstring_logger': No such file or directory
make: *** [install] Error 1


Sounds like you forgot to run make before make install.

As for the voice, you can simply remove any line in autokey.py with this: os.system("espeak.

If you don't feel like doing this yourself, here's a script that'll do the job on an already installed-from-deb setup:

```

#!/bin/sh

sed 's/os.system("espeak '\''\(.*\)'\''.*")/print "\1"/' /usr/bin/autokey.py > /tmp/new_autokey.py
chmod a+x /tmp/new_autokey.py
sudo mv /tmp/new_autokey.py /usr/bin/autokey.py


```

---

### Post by adpads on 2008-02-21
OK, excellent!

Yeah, I figured out that cleverly I did not have make-essential installed. :)
Compiling goes a lot more smoothly with that!

So, I took out the lines containing references to espeak from the script, compiled and installed it, and it is working brilliantly. Now I will settle in to putting all my commonest typos into the abbr.ini file, and I'll keep you posted on how things shape up! A few days of work should really tell us how it handles.

I will probably also try to compile and install this on my little 900-gram Asus eeepc, which runs a xandros debian Linux, and has a tiny little typo-making keyboard. If it works well, I bet this little script would be wildly popular with the eeepc user community. I'll keep you posted on that too, and invite you to go post over there if it works nicely, OK?

A thousand thanks!

a

---

### Post by adpads on 2008-02-21
first observation is that it is doubling the nonalphabetic character that follows the string it replaces, so for example, if I type
 btw,

it gives me
by the way, ,

and similarly depending on what follows the string I get two spaces, periods, etc.

---

### Post by peabody on 2008-02-21
> **adpads said:**
> 
A thousand thanks!


You're welcome.  You could do me a big favor by reading [this](http://ubuntuforums.org/showthread.php?t=703736) thread and getting some publicity for the project, help me look for developers to take over, etc.

---

### Post by peabody on 2008-02-21
> **adpads said:**
> first observation is that it is doubling the nonalphabetic character that follows the string it replaces, so for example, if I type
 btw,

it gives me
by the way, ,

and similarly depending on what follows the string I get two spaces, periods, etc.

[edit sorry I originally said smaller values, but you want the timeout to be higher.  Basically, the higher the timeout, the more you're telling autokey to wait for X to get and process the input].

Sounds like you want to play with the [ timeout ] value.  Run autokey.py from a terminal and pass progressively larger floating point values, such as 0.9 0.99 1.09, etc.

The behavior you describe is basically a race condition in that autokey sees the input before X deals with it and sends the backspaces and expansions before X gets them, so the last characters get sent twice.

---

### Post by adpads on 2008-02-22
.

---

### Post by adpads on 2008-02-22
Sorry, can you clarify how to adjust this timeout value?

Thanks again,
a

---

### Post by adpads on 2008-02-22
ok, sorry to triple post... I have found the value, I'm mucking around with it..

---

