---
title: "Recording Skype"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by Qwerty_ on 2007-08-12
Hi I have been following the instructions over at

[https://help.ubuntu.com/community/SkypeRecordingHowto](https://help.ubuntu.com/community/SkypeRecordingHowto)

To setup Skype to record as I want to use it for podcasting

However when I go to follow

(Note: you can replace gedit with your editor of choice.)

We have now opened up an editor to edit the program. Scroll down until you see my $SKYPEREC edit the value to something like this: /home/yourusernamehere/skype-rec-kraken/libskype-rec.so

I am unable to find $SKYPEREC in the file I think that a newer version of the rec script might of been released


Could someone please direct me as to what I should change.

Many Thanks.

---

### Post by Qwerty_ on 2007-08-12
Err whats your problem? I am just asking what  am I suppose to change since the instructions on the link I provided no longer work, as I was not able to find $SKYPEREC, in which I have to change to where I want to recording to be saved.

---

### Post by MenZa on 2007-08-12
> **bwtranch said:**
> If i didn't make this clear. Let me clear it up for you right now. You can't just hack on somebody else's work. READ THE GNU LICENSE. You worthless little toad. If you do that, I will make sure that you are banned from this forum and your name will be mud. Youi don't do that to people. Maybe you don't understand so you will get a break this one time. Don't let it happen again. :(

Sorry? I don't exactly see what the problem is here? What's Qwerty_ done wrong? And I should also point out that GNU have several licences; the Free Documentation Licence, the General Public Licence and the Lesser General Public Licence, to name a few.

Also, it would appear that the article is under construction, so I'm not sure I would depend too much on it, or even use it.

---

### Post by Qwerty_ on 2007-08-12
Wouldn't be because I posted the code in before I have since removed incase that caused the problem.

Perhaps I will just work out a way to record the output of my sound card.

---

### Post by schorsch on 2007-08-12
You could try this, perhaps it will work:

- open a terminal session
- change to the directory where you have compiled skype-rec
- export SKYPEREC
  ```
export SKYPEREC=/home/yourusernamehere/skype-rec-kraken/libskype-rec.so
```
- run the command "./skype-rec" in the SAME terminal session

If this works just add the export line to your .bash_profile to make it permanent.

---

### Post by Qwerty_ on 2007-08-13
Thanks for the advice schorsch however it does not seem to work some errors with the code.

Terminal output

mike@mike-desktop:~/skype-rec-1.0$ export SKYPEREC=/home/mike/skype-rec-kraken/libskype-rec.so
mike@mike-desktop:~/skype-rec-1.0$ ./skype-rec
Can't locate /home/mike/.skype-rec in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at ./skype-rec line 32.
mike@mike-desktop:~/skype-rec-1.0$ 


Im going to go with plan two, work out how to record the outputs of your sound card, I remeber seeing something somewhere once ill have a look around.

---

### Post by Qwerty_ on 2007-08-13
I am so close to getting this going now. I found a site that has instructions on how to get gnome-sound-recorder to record skype conversations.

[http://porpoisehead.net/hi/?q=node/23](http://porpoisehead.net/hi/?q=node/23)

I have followed it through but got stuck with setting Skype to use alsa have tried leaving as defaults and messing with other options.

I am able to start a skype conversation whilst recording, however once Skype finishes dialing (just before I would start the conversation) I get an input error which I assume is to do with having both the applications running at the same time.

I have tried installing alsa-oss and using skype and sound recorder with aoss (what I do to get Team Speak and games running at the same time) however this has not fixed the problems.

Does anybody have any suggestions?

Cheers

---

