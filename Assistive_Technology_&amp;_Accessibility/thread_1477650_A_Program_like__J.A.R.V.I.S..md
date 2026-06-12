---
title: "A Program like  J.A.R.V.I.S."
date: 2010-05-09
forum: Assistive Technology &amp; Accessibility
---

### Post by mcoleman44 on 2010-05-09
Im there a way to get a program like Jarvis from Iron Man? I can make my own if someone can give me an idea of where to start. Maybe like a program I could play around with and edit. I plan on putting in a bunch of my own if, then, echo statements. Im just not sure what file or program I would edit. 

-Thanks

---

### Post by mcoleman44 on 2010-05-09
It doesnt have to be able to carry on a huge conversation with me, I  just want it to be able to answer questions. Like what is today? Whats  the wether for the next 2 days? I would also like it if it could look  up things on the internet for me. Like if I said "what happened during  WWII?" It would look up wikipedia and read everything to me.

I would also like it to remember things I say. Like if I said "I just paid my bill online, the confirmation code is ##whatever##". And lets say two weeks later I need the confirmation code. Id like to say, "whats was the confirmation code I gave you two weeks ago?". And it read it back to me.

---

### Post by Iowan on 2010-05-09
Moved to Assistive Technology & Accessibility by request.

---

### Post by Sonsum on 2010-05-10
I don't really know anything about programming, but man, do I want this program. lol

---

### Post by Tux.Ice on 2010-05-10
Yea me too. The hardware would be awesome as well.

---

### Post by int2ag0n on 2010-05-20
It would be cool. I had the same idea when i saw the first movie.

But saying that you want just a J.A.R.V.I.S. like program is just too general . Please become more specific , what functionality would jarvis have , with the current technology.

Some functions that first come to mind is , to find something in the web , a youtube video , a wiki , etc , with voice input from the user and voice response from the program.

---

### Post by ubunterooster on 2010-05-20
it is somthing like an advanced [infobot]("http://en.wiktionary.org/wiki/infobot")

---

### Post by Sonsum on 2010-05-20
How about making something that responded to voice commands, could read off twitter and fb updates and possibly was integrated with Wolfram Alpha or Wikipedia.

The voice integration is key here. Make a a virtual butler :)

---

### Post by rao.nischal on 2010-05-20
The key to have a J.A.R.V.I.S like program is to first have speech recognition in linux.

I and some of my friends have developed a speech recognition software called VEDICS (Voice Enabled Desktop Interaction and Control System). It lets the user access any element found on the users screen (accessing files, to links, to buttons... anything). You can find the demo screencasts:

Accessing the panel menu and applications:
[http://www.youtube.com/watch?v=WrVaJXtv0WU](http://www.youtube.com/watch?v=WrVaJXtv0WU)

Changing theme and background:
[http://www.youtube.com/watch?v=zRgX94qGj3g](http://www.youtube.com/watch?v=zRgX94qGj3g)

Navigating directories and playing songs:
[http://www.youtube.com/watch?v=kVQwAoeIavk](http://www.youtube.com/watch?v=kVQwAoeIavk)

Running a slide show:
[http://www.youtube.com/watch?v=JtzA8TFwvuI](http://www.youtube.com/watch?v=JtzA8TFwvuI)

Running default applications and window operations:
[http://www.youtube.com/watch?v=iCEANbu8p50](http://www.youtube.com/watch?v=iCEANbu8p50)

Stopping and starting vedics:
[http://www.youtube.com/watch?v=TLFtdrlt3lM](http://www.youtube.com/watch?v=TLFtdrlt3lM)

Creating and deleting files:
[http://www.youtube.com/watch?v=_3CFAl22h2o](http://www.youtube.com/watch?v=_3CFAl22h2o)

We still have to create an installer. So it would probably be more than a month before we release it. In the meantime you can browse the source code at : [http://sourceforge.net/projects/vedics/](http://sourceforge.net/projects/vedics/)

JARVIS?? hmm... this is something i am sure our team can actually do. May be not immediately, but, say in another 2 years. :)

---

### Post by mcoleman44 on 2010-05-20
@rao.nischal,
I am interested and following your progress and I must say that I'm impressed so far. I think my biggest goal with a Jarvis like program would be to have control over the command line. 

If I can get it to recognize key words it could then compile that into a command. I also really would love if it could remember the things I say and be able to recall them later. 

Like If I needed to give my download folder some free space I would say:
"Jarvis, clean out my downloads folder" Jarvis translates to:
sudo rm -rf Downloads
sudo mkdir Downloads

"Jarvis, tell me about WWII"
sudo apt-get install lynx-cur
lynx [http://en.wikipedia.org/wiki/World_War_II](http://en.wikipedia.org/wiki/World_War_II)

Jarvis would then start at about line 10 and read it all to me.

---

### Post by rao.nischal on 2010-05-21
Such a thing should be possible, though difficult.

1. To recognize commands, the PATH needs to be searched and list of all commands can be searched.

2. Each command has its own syntax and options. Which can be found in the man pages (is there another way??). 

Doing 1 is very easy while doing 2 is the toughest (making a program understand man pages???) 

The part which reads articles is also tough but not impossible. My initial idea was to do google search when the user says "world war 2" and then the user can select a link. Jarvis can then read the contents of that page.

---

### Post by bharatjoshi on 2010-05-21
Hi,
I am from VEDICS team. J.A.R.V.I.S was one of the initial inspiration in developing VEDICS. We thought it would be awesome if we try to atleast do 20% for what JARVIS could do. And we are more than happy with how much we have achieved with VEDICS.
Vedics cant do dictation and pronunciation currently, but it lets you access almost everything in the OS. 

Now coming to what @mcolman44 said, we can definitely add small questions, which vedics can recognize and reply. We plan to add dictation and pronunciation feature to VEDICS in the near future. So what mcolman44 said in his first post is actually very much possible.

But making an application understand the meaning of a sentence and then take appropriate steps, is at present very difficult (not impossible). This feature taps into the field of artificial intelligence, which can be a big project in itself.  
I agree with what NISCHAL said.

---

### Post by mcoleman44 on 2010-05-21
Well, for a more complete program I would agree with both 1 and 2. But my idea is for it to be up to the user which commands are listed and stored by Jarvis. I wouldn't want all utils and commands listed in the program. The user could add only the coomands he/she needs. And then link those commands to key words chosen by the user. 

Something like:
if key words Clean, downloads, folder were heard then it would link those words to a particular command predefined by the user. Then the idea would be for it to echo something like "downloads folder cleaned Mr Coleman" ( I realize that may sound stupid, but I would still enjoy it). 

Another idea would be for it to be connected to a webcam. I use a program called motion that will cause my webcam to take a picture for any movement in sight. If I could get my computer to do certain tasks when the webcam detects motion it would be great. I'm taking a look at your source code right now. I'm a bit sleepy at the moment but if you don't mind Id like to ask you some questions about it tomorrow.

---

### Post by sharath.puranik on 2010-05-21
@coleman:
Hi, I am another developer of VEDICS, sure you can ask us anything about the source code...

and for the rest, what you ask for is actually possible but then the user would have to actually define all the commands himself, which sort of takes away the charm of AI interaction, it would just be a repeater of whatever commands I set.
Also defining/selecting the keywords would be a big headache, if the user customizes it then there are possibilities of clashes... for e.g. if I have Downloads and downloads folders in my home folder, what should be done??
But all said and done, it is still doable...

As for the webcam thing you mentioned, this software created by Lionhead studios does something like that...
[http://www.youtube.com/watch?v=SxU_T7C4Ils](http://www.youtube.com/watch?v=SxU_T7C4Ils)

---

### Post by mcoleman44 on 2010-05-21
I still want the AI bit. I really like the idea of combining voice control and a chatbot/infobot like ubunterooster mentioned. I also think it would be almost impossible to come up with a program to filter my words and options located in the man pages to a final command. It would be programming hell. Which is why it would be nice if the program also had a place to add custom commands to the code. 

As for the Downloads, downloads problem, some logic code would have to be added. Say if I said that, Jarvis would argue that there are two folders by that name. Or since Linux is case sensitive I could have the custom command define Downloads, not downloads. 

And I love the idea of AI, but for a program like this I think a few pre-defined commands are needed. Because let's face it, AI isn't all that ready yet. But I think a combination of the two would work
nicely. Jarvis could learn to converse with me while at the same time being able to function exactly the way I the user would want him too.

---

### Post by tmette on 2010-05-21
Well [this]("http://projectjarvis.com/") is something pretty close.  Although it's done from a Mac Mini, still pretty cool though what this kid has created.  Check out his YouTube vids.

---

### Post by mcoleman44 on 2010-05-21
@tmette, I've seen his videos and his webpage, and I agree that what he has is awesome so far. Problem is, one ist made only for a mac, an two he's been saying he'll make it
open source for a while now, and it's still not. But what he has now is what got me
thinking
this was actualy possible in the first place.

---

### Post by tmette on 2010-05-21
> **mcoleman44 said:**
> @tmette, I've seen his videos and his webpage, and I agree that what he has is awesome so far. Problem is, one ist made only for a mac, an two he's been saying he'll make it
open source for a while now, and it's still not. But what he has now is what got me
thinking
this was actualy possible in the first place.

Yea, I would love to see this become open source.  I do have a MacbookPro but I'm sure it wouldn't take long for something like this to run on Ubuntu if he made it open source on OSX.

---

### Post by jambel on 2010-06-19
Hi all, I'm working on a system like jarvis and hopefully soon open the source.

You can check the project page [http://sites.google.com/site/projectjanet/](http://sites.google.com/site/projectjanet/)

I will open a dedicate post when I'm ready!

Thanks!

---

### Post by jambel on 2010-06-22
> **mcoleman44 said:**
> If I could get my computer to do certain tasks when the webcam detects motion it would be great.

or you can use your cellphone's bluetooth which supported by jaNET 8) 
[**Here**]("C:%5CUsers%5Cj.ambeliotis%5CAppData%5CLocal%5CTemp%5CAppConfig.xml") you can find the responsible file for building custom instructions or command sets which I call.

To get an idea how the project works, check the [**project definition**]("http://sites.google.com/site/projectjanet/project-definition") page.

you can also view some videos **[here]("http://sites.google.com/site/projectjanet/video-gallery")** (they are lame but that's ok).

Maybe we should marry VEDICS and jaNET

---

### Post by jambel on 2010-06-26
Finally I've publish the source code if anyone interested
[http://sites.google.com/site/projectjanet](http://sites.google.com/site/projectjanet)

I also open a dedicated thread [**here**]("http://ubuntuforums.org/showthread.php?p=9513645#post9513645")

---

### Post by pbeesley on 2012-06-18
> **rao.nischal said:**
> 
JARVIS?? hmm... this is something i am sure our team can actually do. May be not immediately, but, say in another 2 years. :)

Your two years are up!!!!!!!!1

---

### Post by overdrank on 2012-06-18
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

