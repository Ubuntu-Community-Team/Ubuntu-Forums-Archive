---
title: "Understanding Audio in Ubuntu"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by Gary Nored on 2006-05-05
Well, I'm on my 6th install of Ubuntu, trying to get sound right. I've read a gazillion threads, done everything I've been told to do, and still no audio. 

I even put in a new soundcard (Turtle Beach Catalina) which played beautifully right out of the box, that is until I installed something. 

Apparently task-oriented instructions are not going to help me until I understand more about Ubuntu, so here are some questions.

1. How, exactly, is sound supposed to be implemented. I know there's ALSO, but how does ALSO know where the sound card is and how does it communicate?

2. Where are the configuration files for ALSA. Where can I find a a copy of what's supposed to be in these files as opposed to what some player puts in them?

3. What is EDS (is that it?). If it's a sound server, where does it reside? Where are its configuration files? How should they be set up. 

4. Aside from Applications-->Audioxx-->Volume Control, how do you control things like input level, output level, etc.

5. If there is a "driver" level and a sound server, how do the two interact? 

6. What kinds of changes might an install do that could break something somewhere else (I had it working for about 30 minutes once -- then I thought I'd try out another player, and boom! No line in).

7. If I install RealPlayer, what does it mean when it asks for "symbolic links?" What should my answer be? Where should I put them?

8. Is there a centralized set of documents that cover these kinds of questions? Believe me I have more. 

I hate to keep asking the same things over and over again, but every time I do something in Ubuntu I seem to get different results! Aaarghh!

Gary:confused:

---

### Post by mostwanted on 2006-05-05
[QUOTE=Gary Nored]Well, I'm on my 6th install of Ubuntu, trying to get sound right. I've read a gazillion threads, done everything I've been told to do, and still no audio. 

I even put in a new soundcard (Turtle Beach Catalina) which played beautifully right out of the box, that is until I installed something. 

Apparently task-oriented instructions are not going to help me until I understand more about Ubuntu, so here are some questions.

1. How, exactly, is sound supposed to be implemented. I know there's ALSO, but how does ALSO know where the sound card is and how does it communicate?

2. Where are the configuration files for ALSA. Where can I find a a copy of what's supposed to be in these files as opposed to what some player puts in them?

3. What is EDS (is that it?). If it's a sound server, where does it reside? Where are its configuration files? How should they be set up. 

4. Aside from Applications-->Audioxx-->Volume Control, how do you control things like input level, output level, etc.

5. If there is a "driver" level and a sound server, how do the two interact? 

6. What kinds of changes might an install do that could break something somewhere else (I had it working for about 30 minutes once -- then I thought I'd try out another player, and boom! No line in).

7. If I install RealPlayer, what does it mean when it asks for "symbolic links?" What should my answer be? Where should I put them?

8. Is there a centralized set of documents that cover these kinds of questions? Believe me I have more. 

I hate to keep asking the same things over and over again, but every time I do something in Ubuntu I seem to get different results! Aaarghh!

Gary:confused:[/QUOTE]

First of all, it would be very helpful if you told us what you installed that ruined everything.

1,2,3. ALSA (not ALSO) is the underlying sound system, ESD is a mixer. Ubuntu uses those to play sounds. As for their configuration files, you probably shouldn't be messing withm them unless you know what you're doing (that, and I have no idea where they are). All of your configuration files and folders are in your home folder prepended with a dot - use Nautilus' option to show hidden files. Try removing .gnome2, that should revert most settings.

4. System &#8594; Preferences &#8594; Sound has some options for system sounds and what sound card to use. Input would probably be application specific. Output can be configured via the volume applet.

5. That's a technical question and I'm not really qualified to explain complicated technical driver interaction :)

6. Could be all sorts of things. Enabling/disabling the sound server is a common cause of malfunctions. Again, I must stress, what did you install?

7.  Hm...  symbolic links are shortcuts or launchers.

8. Not really sure about that. Try looking it up on the wiki.

---

### Post by Gary Nored on 2006-05-05
Well, I think the first time i broke it I was installing AmaroK. I've since re-installed, so there's no chance of going back. I'm basically pretty happy with what comes in the package, but I want Gramofile and I'd like RealPlayer so that I can listen to some European internet radio stations. 

The second time I installed, I followed "intangible"s instructions on this forum for setting up the sound. It was amazing, I finally had line-in! Unhappily, I no longer had line-out. 

It just seems that if I understood the audio system more I could recover from some of these failures.

thanks for your help -- I'm ready to try anything!

Gary

---

### Post by Sef on 2006-05-05
> I'd like RealPlayer so that I can listen to some European internet radio stations. 

I use Rhythmbox to get some European stations.

---

