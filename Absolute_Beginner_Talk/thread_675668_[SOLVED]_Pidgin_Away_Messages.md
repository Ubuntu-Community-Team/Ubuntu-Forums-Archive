---
title: "[SOLVED] Pidgin Away Messages"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by SilverDragon on 2008-01-22
I just have a quick question about Pidgin away messages.

My friend signed onto Pidgin on his screen name and when he went to use an away message he just typed something quickly and clicked "use".

The problem is if you don't click on  "Save & Use" or "Save" your away messages do not appear under your saved messages, which can later be removed easily.

In AIM if you just use and do not save the away message it will be gone once you come back. On Pidgin though, the away message is still there when you go to change your status.

Is there any way to get rid of this away message, because having other people's away messages take up space away from my own saved away messages.

---

### Post by y-lee on 2008-01-22
Never had that problem or never noticed it.

Try editing the **status.xml** file, it should be found in the **/home/username/.purple ** directory. Find the file right click it and open it in a text editor. Find your message and delete the segment of code between the status tags, should look something like below: 

```

<status name='messagename' created='1173443115' lastused='1173443115' usage_count='1'>
		<state>away</state>
		<message>whatever the message was</message>
</status>
```

save your file and try opening pidgin and check whether the message is gone.

should work. tho I've never did it. lol

---

### Post by SilverDragon on 2008-01-23
I tried what you suggested and it worked.

Whenever I went to save it, it would save it would also save a copy, which I thought was strange.

The original file was changed though.

It didn't work at first, because I left pidgin open (oops :cool:) but then I closed it, edited the file, then started pidgin and it worked.

Thank you for very much for your help. 

Now the "why do you have an away message that says your hanging out with yourself?"will stop. :D

---

### Post by y-lee on 2008-01-23
Glad to be of help. I forgot to mention be sure Pidgin is closed but I spaced it out and figured you'd get that part or repost if it didn't work. :)

---

### Post by y-lee on 2008-02-11
I got this in my e-mail not here but my real e-mail. I suppose some one not on this forum tracked me down doing research on the same sort of problem.:lolflag:

It does no harm to add it here as it relates so:  

> Hi y-lee!

Searching for the same help as Silverdragon (deleting status messages in pidgin) I found following question in Developers TRAC:

[http://pidgin.im/pipermail/tracker/2007-May/003501.html](http://pidgin.im/pipermail/tracker/2007-May/003501.html)

which was answered here:

[http://pidgin.im/pipermail/tracker/2007-September/014127.html](http://pidgin.im/pipermail/tracker/2007-September/014127.html)

I tested the suggested solution with pidgin 2.3.1 and it worked.

Perhaps you could add this to the forums ;)



---

