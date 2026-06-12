---
title: "[SOLVED] Menu Bar Question"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by meustrus on 2008-01-03
Very basic, specific question, although indicative of a large issue.

The short question is, where are the configuration files for the menu bar located?

The situation is...I was trying to get rid of some old icons that for one reason or another didn't get uninstalled properly.  So the configuration manager crashed, and now it seems that the entire Applications menu has disappeared from both the menu bar and the main menu button.  I also can't access the settings with the manager by any means, and the problem persists with reboot.

But it's alright if you just answer the simpler question.  I may well be able to solve this on my own if I find out where the configuration files are.

---

### Post by ~LoKe on 2008-01-03
Hm...a shot in the dark perhaps...but gconf-editor?

---

### Post by wolfen69 on 2008-01-03
system>pref>main menu

---

### Post by meustrus on 2008-01-03
That path was one method I tried, and it doesn't work.

gconf-editor is all fine and dandy, but it's like a whole new filesystem and I still don't know my way around it.  I read something about .xbel files on my pre-post search, but didn't catch where they were.

---

### Post by meustrus on 2008-01-03
This isn't quite solved yet...I was impressed with the speed of the first response, but it seems to have dropped off.

---

### Post by meustrus on 2008-01-05
Well, I fixed my own problem eventually.  I believe my applications.menu file was corrupt or destroyed (though I don't know where it is anyway), and alacarte apparently crashes if it can't find the file.  Snooping around I found a launcher for gmenu-simple-editor, which doesn't seem to share alacarte's problem.

Thanks for nothing.  I'll have to remember not to come here next time I have a problem.

---

### Post by buccaneere on 2008-01-05
> **meustrus said:**
> Well, I fixed my own problem eventually.  I believe my applications.menu file was corrupt or destroyed (though I don't know where it is anyway), and alacarte apparently crashes if it can't find the file.  Snooping around I found a launcher for gmenu-simple-editor, which doesn't seem to share alacarte's problem.

Thanks for nothing.  I'll have to remember not to come here next time I have a problem.

Since your problem is solved, then maybe you can help solve some others' problems...

...unless you only want help for yourself, but not TO help others...

---

### Post by ~LoKe on 2008-01-05
> **meustrus said:**
> Thanks for nothing.  I'll have to remember not to come here next time I have a problem.

Because no one tried to help, right? :rolleyes:

---

### Post by meustrus on 2008-01-05
Interesting that I get replies now that it's solved.  Saw it by email notification of subscribed threads.

@buccaneere: Perhaps I'll help people once I know more about Ubuntu.  I've only been playing with it for a couple of months, and I still don't quite understand some of the basic things like getting programs to install from anything besides DEB packages (don't answer it for me, I'm sure I can figure it out and I don't want to ask questions that must have been asked thousands of times before me).  And that might not even make sense anyway...

@LoKe: I wish this didn't sound so harsh, but...helping isn't just about giving your first impression answer and going away, it's about doing that, then listening for further development, then maybe posting again.  But it's a large forum, so I understand that you can't give me any personalized assistance.

What I don't understand is why only you and wolfen69 replied.  The only reason that nobody else would have applied could be that the two solutions are the only ones that anybody who saw this thread could think of, and the others didn't want to repeat you.  Ubuntu forums isn't the only place I've been on the internet, and I've been guilty too of neglecting to say anything unless it was off the top of my head.  All that you can really expect from a fly-by-night member seeking minor assistance like me is that I will like your responses or I won't.  In this case, I didn't like the response, and I hope that since it seems people are paying attention to this thread past now, this thorough response might explain why I didn't like the responses and what you could do in the future so that others are not disappointed like me.

---

### Post by ~LoKe on 2008-01-05
I'm not really sure what to tell you.  You asked where the configurations for the menu bar were kept and were given two likely answers.  Thus, your question was answered.  However, you never said that you even tried getting anywhere with those two options, and just seemed to sit around and wait for us to give you a step by step guide to fix a problem.

But I can understand the frustration, however, I don't understand how you can hold the entire userbase responsible for a single unanswered question.  I suggest you take a look around and see how many people are devoting their time to answering questions and correcting issues, people who are receiving notice in return (with the exception of support from other users).

You had a bad experience, one which you seem to have solved on your own.  Then you damn the forums because of it.

Whatever, though.  That's your opinion and you're entitled to it.

---

### Post by buccaneere on 2008-01-05
Yeah. We all want our problems solved yesterday. And I'm even more impatient than that!

While you're waiting for help (and by the way, look at how many need help, as opposed to have answers), try reading others posts about the same issues.

I've learned about 15 times more stuff from readin' others' posts, than from direct help to my posts. And only about 1 post out of every 12 has real helpful info for anything. What's that tell ya' about how much ya' have to read???


That's why I was readin' your thread...

---

