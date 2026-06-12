---
title: "How to create/modify a keyboard layout?"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by tico on 2007-06-17
Hi,

I'd like to know how to create a new keyboard layout or to modify an existing one. Is there a graphical interface for doing this (in Windows you can use the Keyboard Layout Creator). In Windows I use a modified layout to type Ancient Greek using dead keys (shift, ctrl, alt). I have modified the original polytonic layout that comes in WIndows XP and would like do the same in Ubuntu. How could I do that? And how to make this new layout appear in the Keyboard Preferences window?

Thanks for your help.

---

### Post by kyphi on 2007-06-17
You could try System -> Preferences -> Keyboard -> Layouts, then Add (Greek).  Then click on Layout Options to assign special characters to shift, ctrl and alt.

If you are using special characters now, you may have to create a folder and collect them there.

Alternatively, you may find a better solution in OpenOffice Writer, although I have not tried that myself.

Cheers

---

### Post by strider1551 on 2007-06-17
The Greek Polytonic keyboard is not useful for Ancient Greek.  In Ancient Greek, a vowel can have any combination of an accent, a breathing mark, an a iota subscript.  There are three different accents and two different breathing marks, which means a lot of combinations.  The Windows polytonic keyboard handles this quite nicely, but the Linux plytonic doesn't seem as capable.

There used to be a GTK2 input method called [[COLOR="Blue"]im-classicalgreek[/COLOR]]("http://sourceforge.net/project/showfiles.php?group_id=78185").  Unfortunately, it doesn't work with the current version of GTK2, and the author abandoned the project four years ago.  You can read my experiences in [[COLOR="Blue"]this post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=192357").  The author never returned my email.

Truthfully, I'm not sure if a keyboard layout can be created to suite Ancient Greek because of the limitations of whatever program handles that.  However, I am no expert on this and have yet to sit down and try it myself.  I suggest reading [[COLOR="Blue"]this article[/COLOR]]("http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11").  It doesn't list a graphical utility, but it may get you started.  I believe I heard about a gui somewhere...

Please update this thread if you make progress!  My inability to easily type Greek is the only thing about Linux that has ever let me down.  Personally, the switch is still definitely worth it, I just wish it wasn't an issue.

---

### Post by tico on 2007-06-18
Hi, strider1551,

Well, using Ubuntu with polytonic Greek layout I can type accents, breathing marks and even macron and brachia. The only problem is that I like to make some changes to make this layout easier for me (since I'm used to a modified layout of polytonic Greek in Win XP).
Try again and you'll see that typing ancient Greek is possible in Ubuntu.

---

### Post by strider1551 on 2007-06-18
I have figured out how to get accents, but how do you type something like an alpha with smooth breathing and an acute accent?  For that matter, how do you get the breathing mark to be over the alpha and not in front of it?  It would be great if things have changed since I last looked into this.

---

### Post by tico on 2007-06-18
> **strider1551 said:**
> I have figured out how to get accents, but how do you type something like an alpha with smooth breathing and an acute accent?  For that matter, how do you get the breathing mark to be over the alpha and not in front of it?  It would be great if things have changed since I last looked into this.

Since accents and breathings are dead keys, I need to type: accent+breathing+letter (in this order; if you type breathing before it doesn't work). Try it and tell me if works.

Cheers.

---

### Post by strider1551 on 2007-06-18
Well, it basically gets mad at me.  First I hit the semicolon to get an accute.  Then as soon as I hit shift+semicolon for a breathing mark, I get a system beep.  If I skip the breathing mark, I can correctly get a vowel with accent.

I think the trouble is that the breathing mark isn't being treated as a dead key.  If I just type shift+semicolon, it immediately prints a breathing mark without a letter underneath.

---

### Post by simosx on 2007-06-18
There are efforts to get Linux support for Polytonic working, though we did not have all the contributions required. If you want to assist, we is some info of the current situation.

We need documentation for the keyboard layout for Polytonic. Here is a starting point,
[http://planet.ellak.gr/misc/polytonic/](http://planet.ellak.gr/misc/polytonic/)

There is currently support for Greek Polytonic in Xorg (thus any distro), though you may exhibit some bugs.
1.The typical instructions are 
[http://simos.info/blog/archives/342](http://simos.info/blog/archives/342)
2. Cannot type some of the "accents" in Ubuntu,
[https://bugs.launchpad.net/gtk/+bug/21637](https://bugs.launchpad.net/gtk/+bug/21637)
3. All bug reports for Greek support in Ubuntu at
[https://bugs.launchpad.net/~ubuntu-el-testers/](https://bugs.launchpad.net/~ubuntu-el-testers/)
4. In Linux you can combine (stack) two or more dead keys to produce a final letter. In Windows XP you cannot, you need to specify individual combinations, though utilising quite a lot of keys are dead keys.
5. GTK+ apps have trouble with Greek polytonic due to 
[http://bugzilla.gnome.org/show_bug.cgi?id=321896](http://bugzilla.gnome.org/show_bug.cgi?id=321896)
See (1) for workaround for now.

---

### Post by simosx on 2007-06-18
> **strider1551 said:**
> 
....
I suggest reading [[COLOR="Blue"]this article[/COLOR]]("http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11").  It doesn't list a graphical utility, but it may get you started.  I believe I heard about a gui somewhere...
....


There was a project idea for the Google Summer of Code 2007, for GNOME, to create such a tool. AFAIK, noone picked it up.

Doing the keyboard layout with instructions such as 
[http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11](http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11)
should not be terribly difficult. 
GTK+ applications may not work out of the box for new "compose sequences".

---

### Post by tico on 2007-06-21
Hey, everythink was working for me. I could type Polytonic Greek perfectly. Yesterday I reinstalled Ubuntu and now... I cannot type Polytonic Greek anymore!!!!
What's the matter?!

---

### Post by simosx on 2007-06-21
> **tico said:**
> Hey, everythink was working for me. I could type Polytonic Greek perfectly. Yesterday I reinstalled Ubuntu and now... I cannot type Polytonic Greek anymore!!!!
What's the matter?!

???
Is it the same version of Ubuntu?
How did you enable Greek Polytonic?
Are you using KDE applications or GNOME applications?
When you use GNOME applications, did you right-click in the text box and choose the X Input Method?

---

