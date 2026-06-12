---
title: "Evolution Smileys Busted"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by mlhudson on 2007-04-30
I upgraded to feisty when it came out and it is FABULOUS. I love it.

However, the upgrade busted my email smileys in Evolution. I have no idea what to do to fix them.
I checked the "obvious" spots like preferences in Evolution & the system Theme (human). But, I can't find a way to fix it. I also can't find a post that addresses it.

Any ideas for a fix?

---

### Post by Seisen on 2007-04-30
Did the email smilies come installed on evolution?

---

### Post by mlhudson on 2007-04-30
So far as I know they did. I didn't do anything to put smileys there. The just appeared at my first typing of :)
Now I get a little box w/ a red X in it in their stead.

---

### Post by Seisen on 2007-04-30
Have you tried putting smilies in the email from the menu or does that not work either.

---

### Post by mlhudson on 2007-04-30
that was a helpful question. I CAN insert from the menu. but the automatic transformation from the : ) to :) does not generate the image.

I would love to go back to having the automatic smiley.

---

### Post by bapoumba on 2007-04-30
Hello :)
In > Edit > Preferences > Composer > do you have "format in html" ticked ?
When composing a message > Format > html if not ticked in previous menu.

---

### Post by useResa on 2007-04-30
> **bapoumba said:**
> Hello :)
In > Edit > Preferences > Composer > do you have "format in html" ticked ?
When composing a message > Format > html if not ticked in previous menu.
I have exactly the same problem. After the upgrade to feisty the "automatic" smileys stopped working but inserting by using the menu works.

I have the options as indicated above set, therefore this seems not be the cause of the problem.

Any other suggestions for getting the "automatic" smileys back working?

---

### Post by mlhudson on 2007-04-30
HTML formatting is on in both areas. In fact, it seems that the email wants to put the smiley in, but I get the red X where it should go. I can manually insert it, but it doesn't put it in automatically.

---

### Post by bapoumba on 2007-04-30
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gtkhtml3.14/+bug/91149](https://bugs.launchpad.net/ubuntu/+source/gtkhtml3.14/+bug/91149) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **useResa said:**
> I have exactly the same problem. After the upgrade to feisty the "automatic" smileys stopped working but inserting by using the menu works.
I cannot really tell, as I never use html mails. I just checked it for the OP.
> **useResa said:**
> 
Any other suggestions for getting the "automatic" smileys back working?
Please check the confirmed bug report. It's been forwarded to GNOME.

---

### Post by useResa on 2007-04-30
> **bapoumba said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gtkhtml3.14/+bug/91149](https://bugs.launchpad.net/ubuntu/+source/gtkhtml3.14/+bug/91149) 
Thank you for the link, this indeed is the problem
                
> **bapoumba said:**
> It's been forwarded to GNOME.
Does this mean that the fix is "out of the hands" of Ubuntu?

---

### Post by bapoumba on 2007-04-30
> **useResa said:**
> Thank you for the link, this indeed is the problem
Does this mean that the fix is "out of the hands" of Ubuntu?
You're welcome.
Looking at the [GNOME bug]("http://bugzilla.gnome.org/show_bug.cgi?id=419350"), a fix was released but it appears its not working in feisty. You may want to comment in the LP bug (I guess the fix will come as an evolution update)
As far as saying who's hands are on this, I do not know. Its collaborative work :)

---

### Post by useResa on 2007-04-30
> **bapoumba said:**
> You're welcome.
Looking at the [GNOME bug]("http://bugzilla.gnome.org/show_bug.cgi?id=419350"), a fix was released but it appears its not working in feisty. You may want to comment in the LP bug (I guess the fix will come as an evolution update)
As far as saying who's hands are on this, I do not know. Its collaborative work :)
Comment added to both the GNOME bug and the LP bug (thanks for the hint).

---

### Post by bapoumba on 2007-04-30
> **useResa said:**
> Comment added to both the GNOME bug and the LP bug (thanks for the hint).
Yes, that was the best to do. I had second thoughts, reading the bugs over and was about to suggest comments in both, due to the version release numbers (I did not keep tracks with evolution updates so I'm not sure what the diffs are).

---

### Post by rjmarshall on 2008-03-10
I was having this problem on Gutsy as well, it appears that gtkhtml-3.14 was installed, but /usr/share/gtkhtml-3.8/icons is also there and all of the smileys, emoticons, are there, so I just created links in the 3.14 directory and it now works.  I'm sure that an official patch is either available or on its way, but in the meantime...I'm :) in email again.

Rob

---

### Post by z_diver on 2008-03-22
Thanks for the info.  I did not have gtkhtml-3.8 installed in my fresh Gutsy install so I installed that AND then copied the extra image files from /usr/share/gtkhtml3.8/icons into /usr/share/gtkhtml-3.14/icons to make sure I have the smilies working.  Seems like an easy thing for someone to patch.

---

