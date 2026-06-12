---
title: "BASH SCRIPT to Record your Desktop, post on Youtube or other"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by nb123 on 2007-09-21
Hi all, I just wrote my first bash script! I'm very new to linux, so please give me suggestions on how to improve the script. I'm not sure how useful this is, but here it goes!

This script is for anyone who'd like to capture their desktop in action as an .ogg file, convert this .ogg file to an .avi file, add an mp3 file to it and post it on youtube or some other site. Help spread the word on the beautiful beryl/compiz/compiz-fusion effects and linux in general!

Simply download this script to your desktop and copy the following command into your terminal to execute it: ---

chmod u+x /home/`whoami`/Desktop/recorddesk.sh && /home/`whoami`/Desktop/recorddesk.sh

Have fun! And once again, any recommendations on how to improve it would be great, especially the error checking.

UPDATED: ---
The bash script now prompts you to download the required packages if you need to.
It now has better error checking and many more features. Check it out!

---

### Post by HokeyFry on 2007-09-21
I think I will try this out and see how it works. However you say in the file that you should install two programs prior to running this. You should ask if they should be automatically installed if they already are not. I don't know much about bash scripting myself, but I am sure you an easily figure out how to do that

---

### Post by Dr Small on 2007-09-21
All you would have to do, is run
```
sh recorddesk.sh
```
to run the script, but I like how you interrogated `whoami` into your above chmod scipt.

I will check it out later.

Dr Small

---

### Post by HokeyFry on 2007-09-21
something else i would add, if the directory you wish to create is not there, you should have it create it using 'mkdir'

and also, running it like 'sh recorddesk.sh' gives you an error
running it as './recorddesk.sh' does not

---

### Post by HokeyFry on 2007-09-21
awesome, dude, the only issues id fix are these:

- if the directory is not created, create it for the user
- if no music is specified, don't try to append sound to it
- ask the user if they want to convert to the avi format
- add support for other types of sounds

otherwise, it works great. good job!
if you do update it, PM me, or post it up, im interested in whatever your latest version is

---

### Post by nb123 on 2007-09-21
Thanks for the input, okay I've added an option in the script to download the required packages. I think the mkdir idea is definitely something I should put in, but I'm not sure I know enough to handle the errors correctly, in case a user tries to create a folder where he doesn't have permissions to do so, but I'll look up how to do this and update the script when I'm done. 

Also the 'sh recorddesk.sh' command doesn't work like you say HokeyFry cos it's not recognizing the 'select' loop... interesting, I'll have to read up on that, but for now, off to grab myself a beer

---

### Post by nb123 on 2007-09-21
Glad it worked! I like all your suggestions, I'll be looking up how to incorporate them into the script

---

### Post by HokeyFry on 2007-09-21
wish i could have a beer... oh well MD game fuel is good for now ;)


hmm i wonder... is there a way for one to get a GUI from a bash script....

---

### Post by nb123 on 2007-09-22
I have improved the bash script with better error checking and features. I will continue to update it as I work on it. Please scroll to the top and download the attachment, I hope it works for you too. As always, please post any suggestions you might have, thanks

---

### Post by Dr Small on 2007-09-22
> **HokeyFry said:**
> wish i could have a beer... oh well MD game fuel is good for now ;)


hmm i wonder... is there a way for one to get a GUI from a bash script....
Maybe something like this:
```
export DISPLAY=:0
```

??

Dr Small

---

### Post by nb123 on 2007-09-22
Ok, just updated the attachment, sorry about the delay

---

### Post by Fanin on 2007-11-10
this is an awesome program, dude. I've been looking for something like this for a long time =D>
there's just one small problem. When I make a video following the tutorial (great tut by the way) and add an mp3 song, it makes this weird disturbing sound

this is a link to a small video I made (with that sound)
[http://www.youtube.com/watch?v=dbT4aw0ba_E]("http://www.youtube.com/watch?v=dbT4aw0ba_E")

am I the only one having this problem?
does anyone know how to fix this?
:confused:

---

### Post by Fanin on 2007-11-13
anybody? :neutral:
ok, nevermind then :/

---

### Post by nb123 on 2007-11-28
Hi, Glad you liked it! hmmm.. I saw the youtube video, I see what you're talking about, I'm not really sure why... the only thing I can think of is that the mp3 file was damaged? Have you tried making another video with another mp3 file? Still having the same problem?

---

### Post by nb123 on 2007-11-28
I'm not sure whether this could be a problem, I'll have to look at the script again, but perhaps your microphone was enabled when recording the desktop, so it added audio input to the file, and then adding the mp3 file to it later caused the distortion?

---

### Post by Fanin on 2007-12-02
> **nb123 said:**
> Hi, Glad you liked it! hmmm.. I saw the youtube video, I see what you're talking about, I'm not really sure why... the only thing I can think of is that the mp3 file was damaged? Have you tried making another video with another mp3 file? Still having the same problem?

> **nb123 said:**
> I'm not sure whether this could be a problem, I'll have to look at the script again, but perhaps your microphone was enabled when recording the desktop, so it added audio input to the file, and then adding the mp3 file to it later caused the distortion?

I tried again with a muted microphone, yet the same problem occurred
[_video with no mic_]("http://www.youtube.com/watch?v=WLxvOestVxw")
so it must be that the mp3 is damaged :(

---

### Post by nb123 on 2007-12-02
Yeah, that's the only thing I can think of, I had some problems with another mp3 file as well.... the mp3 file didn't seem to be damaged, yet I just couldn't add it to the video, maybe someone with more experience can help explain this?

---

### Post by Fanin on 2007-12-04
> **nb123 said:**
> Yeah, that's the only thing I can think of, I had some problems with another mp3 file as well.... the mp3 file didn't seem to be damaged, yet I just couldn't add it to the video, maybe someone with more experience can help explain this?

I had that very same thing with one of my mp3's.. I tried it twice, but it didn't work, but I just gave up (thinking it was something I did)
btw.. all my mp3's run perfectly fine on Amarok.. not sure they're damaged.. If they were then it shouldn't work, right? :confused:

one more thing.. where did you learn about scripting like that?.. I just need to know :)

---

### Post by jaybombalous on 2007-12-04
try using a mp3 that doesn't have a variable bitrate. U need special support for variable bitrate and being I am not sure what app u are using to add in sound u may or may not have that support.

BTW, I did not look at the bash script, so I am only guessing.

---

### Post by nb123 on 2007-12-05
Thanks jaybombalous for your insight, maybe that's the problem. 

Fanin - I just searched online on how to write bash scripts, like basic commands, and then used other online sites to refer to when I didn't know what command to use. For more experienced bash programmers, my code would probably look very verbose and clumsy, but it does the job! You can just search in google on how to do bash programming in linux and you'll find all the information you need. If you do end up writing a program, please let me know, I'd be sure to check it out

btw, someone else who checked my script out mentioned that he/she was trying to do a GUI for it, that'll be interesting...

---

### Post by Fanin on 2007-12-05
> **nb123 said:**
> Thanks jaybombalous for your insight, maybe that's the problem. 

Fanin - I just searched online on how to write bash scripts, like basic commands, and then used other online sites to refer to when I didn't know what command to use. For more experienced bash programmers, my code would probably look very verbose and clumsy, but it does the job! You can just search in google on how to do bash programming in linux and you'll find all the information you need. If you do end up writing a program, please let me know, I'd be sure to check it out

btw, someone else who checked my script out mentioned that he/she was trying to do a GUI for it, that'll be interesting...

thanks, have to remember to look into bash scripting.. I tried some time ago but ended up learning about Python (which is really fun so far :) ) but i also want to know about bash scripting.
and making this into GUI would be FRIGGIN' AWESOME :biggrin:

---

