---
title: "google2ubuntu"
date: 2014-01-26
forum: Assistive Technology &amp; Accessibility
---

### Post by benoitfra on 2014-01-26
Hello 

first of all, sorry for my poor english. I'm a french student.

I'm here in order to show you a little application i've made: google2ubuntu.
It's a tool that let you use the Google voice recognition api to control you pc. I began to work on it at the beginning of 2012. Unfortunnaly, I've concentrated myself on my studies. Now, I can work.

Now the tool work quite well, it's use is very simple. It records your voice during 5 secondes then sends it to Google (In Python). Google brings you the traduction. In order to manage commands, I've made a little gui (also in Python). For the moment, it's ready for french language. I hope to begin the traduction in english during this week.

When the traduction will end, I'm going to post all technical details about how it work, how to write a module.

The project is available here : [https://github.com/benoitfragit/google2ubuntu](https://github.com/benoitfragit/google2ubuntu)
The project began here: [http://forum.ubuntu-fr.org/viewtopic.php?id=804211&p=1](http://forum.ubuntu-fr.org/viewtopic.php?id=804211&p=1)

I've posted some videos:
[http://www.youtube.com/watch?v=P9c8a4gXbsw](http://www.youtube.com/watch?v=P9c8a4gXbsw)
[http://youtu.be/N2oFlxU5Vwk](http://youtu.be/N2oFlxU5Vwk)

Some screenshots here:

[[IMG]http://pix.toile-libre.org/upload/img/1390673400.png[/IMG]]("http://pix.toile-libre.org/?img=1390673400.png")
[[IMG]http://pix.toile-libre.org/upload/thumb/1390673152.png[/IMG]]("http://pix.toile-libre.org/?img=1390673152.png") [[IMG]http://pix.toile-libre.org/upload/thumb/1390673197.png[/IMG]]("http://pix.toile-libre.org/?img=1390673197.png") [[IMG]http://pix.toile-libre.org/upload/thumb/1390673223.png[/IMG]]("http://pix.toile-libre.org/?img=1390673223.png")

---

### Post by benoitfra on 2014-01-28
There is a ppa (only in french for the moment):
```

sudo add-apt-repository ppa:benoitfra/google2ubuntu
sudo apt-get update
sudo apt-get install google2ubuntu

```

I'm looking for some help for internationalize my work.

---

### Post by benoitfra on 2014-01-29
I'm prouod to announce you that google2ubuntu is now disponible in english. Does anybody want to test and make a video for the english communoty (My english accent is very bad)

---

### Post by bboyjkang on 2014-01-29
Palaver Speech Recognition
Speech Commands for Linux.
[https://plus.google.com/u/0/communities/117295420902112738135](https://plus.google.com/u/0/communities/117295420902112738135)
 
LiSpeak - Linux Voice Command System
[https://plus.google.com/u/0/communities/115594832299044979120](https://plus.google.com/u/0/communities/115594832299044979120)
 
I saw your posts on Google plus. I see a lot of Spanish posts on the Palaver Google plus community, but I can read them because Google plus can translate the messages for me. Since you speak French, Google’s translation can help you check out these 2 projects just in case there are things in common.

---

### Post by Sef on 2014-01-29
Moved to the cafe

---

### Post by benoitfra on 2014-01-30
Thx bboyJKang for these two links, I know Palaver but liSpeak no. There is many thing in common between those 2 systems ?

---

### Post by benoitfra on 2014-01-30
I ve made a new version that include google tts and clipboar tts. Everything is on Github and will be available soon on my ppa

---

### Post by benoitfra on 2014-01-30
I've made a video to show how it work (it's in french):
[http://youtu.be/AaMbJGZBiZ0](http://youtu.be/AaMbJGZBiZ0)
Does anybody want to try and make a vidéo in english ?

---

### Post by 3rdalbum on 2014-01-31
Man, I had this idea years ago but I lack the programming skills to actually make it work. Well done!

---

### Post by benoitfra on 2014-02-04
I've made a lot of work and the project is now available in english. I've written the home page on [https://github.com/benoitfragit/google2ubuntu](https://github.com/benoitfragit/google2ubuntu). 

A ppa is available and you can install google2ubuntu by typing:
```

sudo add-apt repository ppa:benoitfra/google2ubuntu
sudo apt-get update
sudo apt-get install google2ubuntu

```

Now google2ubuntu can read the selected text, tell you the time and the battery amount, find your way on google map, tell you the meaning of a word...control opened windows, launch applications, make search on google, youtube, wikipedia...play all commands you want.

I'm looking for someone to make an video in english. If you are intersted please visits the google+ community:
[https://s://plus.google.com/u/0/communities/103854623082229435165](https://s://plus.google.com/u/0/communities/103854623082229435165)

---

### Post by nilarimogard2 on 2014-02-05
Can you please update the PPA with packages for other Ubuntu versions (as currently only Saucy packages are available)? Thanks!

---

### Post by Linuxratty on 2014-02-05
This has so much potential! Great idea.

---

### Post by benoitfra on 2014-02-05
I will try to publish a version for ubuntu 13.04 and ubuntu 14.04 soon

---

### Post by nilarimogard2 on 2014-02-05
Thanks! By the way, I wrote an article about Google2Ubuntu on WebUpd8: [http://www.webupd8.org/2014/02/linux-speech-recognition-using-google.html](http://www.webupd8.org/2014/02/linux-speech-recognition-using-google.html)

---

### Post by benoitfra on 2014-02-05
T[SIZE=4]hank you very much [COLOR=#DD4814][COLOR=#000000][nilarimogard2]("http://ubuntuforums.org/member.php?u=1858741")  and webupd8[/COLOR][/COLOR][/SIZE]

---

### Post by benoitfra on 2014-02-05
Ok thx to Launchpad I've added a quantal and a trusty entry in the repo.

---

### Post by Chelidze on 2014-02-08
awesome project hope it grows 

Thank you

Meanwhile has anyone added bunch of commends to it and is willing to share  it with me ??

---

### Post by benoitfra on 2014-02-08
Hello from France

I've published the new version of google2ubuntu on my ppa.

It embed two new internal commands that let you use a dictation mode. The dictation mode will automatically write all the text you pronounce, it's note continuous dictation, you will need to restart google2ubuntu for each sentence.

If you want to add those command, add a internal command to enter in the dictation mode 
key = the sentence you want
action = dictation mode

an an other to exit:
key = the sentence you want
action = exit dictation mode

TRANSLATION
Now google2ubuntu embed a very pleasant way to change local on the fly. A little menu on the right let you switch language. (For the gui the change take effect when you will restart it)
Supported language are now:
french
english
spanish
italian
deutch

Someone ask me to add russian translation but I've got the skill to do so I'm looking for some help

---

### Post by Chelidze on 2014-02-09
Sorry for bothering you.

I have a question is there a possibility you can add music search function (rhythmicbox, or other music software) to your project ??
I tried to do so but sadly my skills are nonexistent so I failed miserably so is there a chance you are planning, adding this function to your project??

Thank you in advanced

---

### Post by benoitfra on 2014-02-10
HI

So what you should do is writing a module. A module is basically a script that will receive some text in parameter. 

* First step: write the script
You know what you want search for a song ok it is so you will call the script with the name of the music in argument after you will have to make rhythmbox play this song, I will help you (I can't do the rest because I havn't got rhythmbox)

So an exemple of module (it can be improve a lot):

```

#!/bin/bash
#here we get the text that google2ubuntu will send to the module
URI=$1

#then we proceed and launch the music
MUSIC=$(locate -i ~/Music | egrep -i '\.(mp3|ogg)$' | grep "$URI")
rhythmbox-client --play-uri="$MUZIC";
rhythmbox-client --play

```

* Try the new module and add it to google2ubunt
Done, so you will I to try that before I put it in google2ubuntu. HOW ? Open a terminal and go to the folder containing this script (music has to be mp3 or ogg)

```

cd <path_to_this_module>/
chmod +x module.sh

./module.sh <title of the music>

```

Then once the test is ok I will help you to add this module to google2ubuntu (it is very easy) and I will integrate it by default in google2ubuntu

---

### Post by ibjsb4 on 2014-02-10
Nice :)

I think your thread belongs in Assistive Technology instead of The Cafe.

---

### Post by benoitfra on 2014-02-10
It was in Assistive technology but it was moved

---

### Post by ibjsb4 on 2014-02-10
I do not think 'assistive technology' gets enough support.  PM me if I can help.

---

### Post by Chelidze on 2014-02-10
> **benoitfra said:**
> HI

So what you should do is writing a module. A module is basically a script that will receive some text in parameter. 

```

#!/bin/bash
#here we get the text that google2ubuntu will send to the module
URI=$1

#then we proceed and launch the music
MUSIC=$(locate -i ~/Music | egrep -i '\.(mp3|ogg)$' | grep "$URI")
rhythmbox-client --play-uri="$MUZIC";
rhythmbox-client --play

```

* Try the new module and add it to google2ubunt
Done, so you will I to try that before I put it in google2ubuntu. HOW ? Open a terminal and go to the folder containing this script (music has to be mp3 or ogg)

```

cd <path_to_this_module>/
chmod +x module.sh

./module.sh <title of the music>

```

Then once the test is ok I will help you to add this module to google2ubuntu (it is very easy) and I will integrate it by default in google2ubuntu

Thank you so much for the reply but you are dealing with a real dilettante here.

```
[COLOR=#000000][FONT=Ubuntu Mono]MUSIC=$(locate -i ~/Music | egrep -i '\.(mp3|ogg)$' | grep "$URI")[/FONT][/COLOR]
```

Ok is this part were **[COLOR=#000000][FONT=Ubuntu Mono]locate -i ~/Music [/FONT][/COLOR]**I should specify my music folder location ??

my file looks like something like this 

```
#!/bin/bashURI=$1


MUSIC=$(locate -i '/media/levan/BEEA60D8EA608E89/Downloads/Music/MOR' | egrep -i '\.(mp3|ogg)$' | grep "$URI")
rhythmbox-client --play-uri="$MUZIC";
rhythmbox-client --play
```

When I say the keyword and the music I want to play it just plays the first song in rhythmicbox library and the google2ubuntu notification hangs.

---

### Post by benoitfra on 2014-02-10
Hello

[COLOR=#000000][FONT=Ubuntu Mono]```
MUSIC=$(locate -i ~/Music | egrep -i '\.(mp3|ogg)$' | grep "$URI")
```

[/FONT][/COLOR]this line should search in the folder you mention your music where music is the path

If the player doesn''t play your music it's because that line doesn't find your file so MUSIC=''
So rhythmbox only start and play the first song. I'm looking for improvement this scriptI

---

### Post by benoitfra on 2014-02-10
```

#!/bin/bash
URI="$1"
echo "url = $URI"


FOLDER="$HOME/Musique"
#then we proceed and launch the music
MUSIC=$(ls -d -1 "$FOLDER"/* | egrep -i '\.(mp3|ogg)$' | grep "$URI")
echo "music = $MUSIC"


rhythmbox-client --play-source="$MUZIC";
rhythmbox-clien --play

```

So maybe you can try this one I replace locate by ls in order not to have this problem I've tried the command (not the script I can't I haven't go rhythmbox) with a music on my computer redemption_song.mp3. I've executed:

[CODE]
./rhythmbox.sh redemption
[CODE]

---

### Post by volkerbradley on 2014-02-10
I found this English video:
[http://www.youtube.com/watch?v=HfrQrjH3AGw#t=280](http://www.youtube.com/watch?v=HfrQrjH3AGw#t=280)
In this video, there is a demonstration of dictation mode.  When I say "Dication Mode" in Google2Ubuntu, I see "Error: Setup file missing"
Can you tell me how to enable dication mode?

---

### Post by benoitfra on 2014-02-10
this video is not from me .
In my logiciel if you want do start dictatin mode you have to say dictation mode. When you will relauch google2ubuntu everythin you will say is going to be typing. If you say exit dictation mode you will exit dictation mode

---

### Post by benoitfra on 2014-02-10
Oops I forgot to tell how to add this commans.

* dictation mode
* exit dictation mode

Are internal commands so you need to add them:

1. Click the menu near the add button
[IMG]http://pix.toile-libre.org/upload/original/1392059985.png[/IMG]

2. Select internal command

3 Complete the new line that appears at the bottom of the treeview

[IMG]http://pix.toile-libre.org/upload/original/1392060259.png[/IMG]

Replace "word" by "dictation mode" or "exit dictation mode" and "key sentence" by the sentence you want to pronounce to enter in dictation mode


Then launch google2ubuntu and say the sentence to enter in dictation mode.

---

### Post by Chelidze on 2014-02-10
> **benoitfra said:**
> ```

#!/bin/bash
URI="$1"
echo "url = $URI"


FOLDER="$HOME/Musique"
#then we proceed and launch the music
MUSIC=$(ls -d -1 "$FOLDER"/* | egrep -i '\.(mp3|ogg)$' | grep "$URI")
echo "music = $MUSIC"


rhythmbox-client --play-source="$MUZIC";
rhythmbox-clien --play

```

So maybe you can try this one I replace locate by ls in order not to have this problem I've tried the command (not the script I can't I haven't go rhythmbox) with a music on my computer redemption_song.mp3. I've executed:

```

./rhythmbox.sh redemption
[CODE]


Thank you for the reply but sadly this is what I got maybe I am doing something wrong 

This is the commend I used and this is what I got 

[CODE]#!/bin/bashURI="$1"
echo "url = $URI"




FOLDER="/home/levan/Music/"
#then we proceed and launch the music
MUSIC=$(ls -d -1 "$FOLDER"/* | egrep -i '\.(mp3|ogg)$' | grep "$URI")
echo "music = $MUSIC"




rhythmbox-client --play-source="$MUZIC";
rhythmbox-clien --play
```

 [http://ubuntuone.com/647zYDPnLxbJS0zyKDFimN](http://ubuntuone.com/647zYDPnLxbJS0zyKDFimN)

If it does not work hell with it I can live without it :)

---

### Post by benoitfra on 2014-02-10
it seems that the module keep the execution hand it is why the notification doesn(t desapear.

THANK YOU FOR THE VIDEO IT IS EASIER WITH THAT

Can you show me how you have configurate the module ie the args file and the line you addto google2ubuntu-manger

I have an other question: does other command works you are the first that made a video (other than me)

---

### Post by benoitfra on 2014-02-10
So you find a bug. (Module that keep the execution hand, it will be corrected in the next version, I ve forgot a &)

i spend for you response

---

### Post by benoitfra on 2014-02-10
So you find a bug. (Module that keep the execution hand, it will be corrected in the next version, I ve forgot a &)

i spend for your answer

---

### Post by benoitfra on 2014-02-10
I saw that you have added a module music/music.sh and the args file is here. As you can see rhythmbox was launch but it doesn't play the sound so maybe the module not work.

---

### Post by Chelidze on 2014-02-10
> **benoitfra said:**
> it seems that the module keep the execution hand it is why the notification doesn(t desapear.

THANK YOU FOR THE VIDEO IT IS EASIER WITH THAT

Can you show me how you have configurate the module ie the args file and the line you addto google2ubuntu-manger

I have an other question: does other command works you are the first that made a video (other than me)


This is how it looks 

[IMG]http://i.imgur.com/21YD9At.png[/IMG]

Yes the commends that I've tried they work except wikipedia, I even tried renaming it but it still did not work

About that notification that does not wants to disappear, not all commends have that problem only some commends that I have added poorly have

---

### Post by benoitfra on 2014-02-10
Module keep the execution process the problem will be solve the next version, I ve tried with xdg-open (launch the default music player) ( also try with cvlc it works too)
```

#!/bin/bash
URI="$1"
echo "url = $URI"

FOLDER="$HOME/Musique"
#then we proceed and launch the music
MUSIC=$(ls -d -1 "$FOLDER"/* | egrep -i '\.(mp3|ogg)$' | grep "$URI")
echo "music = $MUSIC"

#rhythmbox-client --play-source="$MUZIC";
#rhythmbox-clien --play
xdg-open "$MUSIC" &

```

I add this module and it works for me. The main problem that I have to deal with is the name of the music. I mean for my music redemption song.mp3. I say "lancer musique redemption song" and it launch ~/redemption song.mp3

But be aware that the module receive letter in lowercase and without accent. So if the title contains (capital letter) ABC.mp3 it coulds leads to some issue even if you pronounce ABC the module will receive abc. Maybe it is hard to understant. I don't know if I'm understanble

EDIT: Maybe it also works with rhythmbox there is a mistake MUZIC should be MUSIC

---

### Post by Chelidze on 2014-02-10
> **benoitfra said:**
> Module keep the execution process the problem will be solve the next version, I ve tried with xdg-open (launch the default music player) ( also try with cvlc it works too)
```

#!/bin/bash
URI="$1"
echo "url = $URI"

FOLDER="$HOME/Musique"
#then we proceed and launch the music
MUSIC=$(ls -d -1 "$FOLDER"/* | egrep -i '\.(mp3|ogg)$' | grep "$URI")
echo "music = $MUSIC"

#rhythmbox-client --play-source="$MUZIC";
#rhythmbox-clien --play
xdg-open "$MUSIC" &

```

I add this module and it works for me. The main problem that I have to deal with is the name of the music. I mean for my music redemption song.mp3. I say "lancer musique redemption song" and it launch ~/redemption song.mp3

But be aware that the module receive letter in lowercase and without accent. So if the title contains (capital letter) ABC.mp3 it coulds leads to some issue even if you pronounce ABC the module will receive abc. Maybe it is hard to understant. I don't know if I'm understanble

EDIT: Maybe it also works with rhythmbox there is a mistake MUZIC should be MUSIC

I experienced very strange thing take a look :D

[http://ubuntuone.com/0CNcRo21Li3QjEstpY2gzR](http://ubuntuone.com/0CNcRo21Li3QjEstpY2gzR)

strange

and this video how is it seeking throe rhythmic box library ??

[http://ubuntuone.com/2Wzmy26xZFApnu0ZS5DMR9](http://ubuntuone.com/2Wzmy26xZFApnu0ZS5DMR9)

---

### Post by volkerbradley on 2014-02-10
Awesome.  Works well.
Thank you very much.
Volker

---

### Post by benoitfra on 2014-02-11
@chelidze

it seems that it wantsto launch the module. But it can't read the file please lauch tha command in the terminal and show me what you will got

```
/usr/share/google2ubuntu/google2ubuntu.py
```

say music test

and post the result

---

### Post by Elfy on 2014-02-11
> **ibjsb4 said:**
> Nice :)

I think your thread belongs in Assistive Technology instead of The Cafe.

> **benoitfra said:**
> It was in Assistive technology but it was moved

It was more chat than not at the time. For the future, use either the Report Button, to talk to us,  or create a thread in [http://ubuntuforums.org/forumdisplay.php?f=123](http://ubuntuforums.org/forumdisplay.php?f=123) to do so. 

We rarely bite... 

In the meantime

*Thread moved to **(Assistive Technology & Accessibility)**.*

---

### Post by Chelidze on 2014-02-11
> **benoitfra said:**
> @chelidze

it seems that it wantsto launch the module. But it can't read the file please lauch tha command in the terminal and show me what you will got

```
/usr/share/google2ubuntu/google2ubuntu.py
```

say music test

and post the result


 YAY :D it worked 

here is terminal output

[ATTACH]250263[/ATTACH]

I have a question I know I am being ungrateful person now and I apologize for that, but is there a chance that you can add that dictation mode that a person posted in this thread ??

---

### Post by benoitfra on 2014-02-11
type or dictation mode ? because dictation mode is already inside

---

### Post by Chelidze on 2014-02-11
> **benoitfra said:**
> type or dictation mode ? because dictation mode is already inside


I tried to do it like this but it did not work

[http://ubuntuforums.org/showthread.php?t=2201895&page=3&p=12925614#post12925614](http://ubuntuforums.org/showthread.php?t=2201895&page=3&p=12925614#post12925614)

---

### Post by benoitfra on 2014-02-11
Curious because even in english in my computer it works.

So add 2 internal commands:
<your sentence 1> : dictation mode
<your sentence> : exit dictation mode

Then say <your sentence 1>, now google2ubuntu is in dictation mode
Click in a input text capable window and speak
To quit say <your sentence 2>

It works for me !

---

### Post by Chelidze on 2014-02-11
> **benoitfra said:**
> Curious because even in english in my computer it works.

So add 2 internal commands:
<your sentence 1> : dictation mode
<your sentence> : exit dictation mode

Then say <your sentence 1>, now google2ubuntu is in dictation mode
Click in a input text capable window and speak
To quit say <your sentence 2>

It works for me !


I will retire, to make it a bit clear I should not add new module in folder just add a new commend in google2ubuntu  menu,

---

### Post by benoitfra on 2014-02-11
yes not a module, those function are implemented in google2ubuntu by default.
So there is (in english):
* dictation mode
* exit dictation mode

You attribute a key sentence for each of those internal commands and then you just have to say those sentence to enter or exit the dictation mode.

---

### Post by Chelidze on 2014-02-11
> **benoitfra said:**
> yes not a module, those function are implemented in google2ubuntu by default.
So there is (in english):
* dictation mode
* exit dictation mode

You attribute a key sentence for each of those internal commands and then you just have to say those sentence to enter or exit the dictation mode.

this is what I get 

[IMG]http://i.imgur.com/AhKVHSXl.png[/IMG]

```
/usr/share/google2ubuntu/resources/sound.wav:

 File Size: 55.0k     Bit Rate: 708k
  Encoding: Signed PCM    
  Channels: 2 @ 16-bit   
Samplerate: 22050Hz      
Replaygain: off         
  Duration: 00:00:00.62  


In:100%  00:00:00.62 [00:00:00.00] Out:13.7k [ -====|====- ]        Clip:0    
Done.
config file: /home/levan/.config/google2ubuntu/google2ubuntu.xml
external dictation mode
sh: 1: dictation: not found



```

---

### Post by benoitfra on 2014-02-11
I've tried (in english now) and it works

Maybe you have added external commands. So it (python) try to launch :
os.system(dictation mode)
that lead to your bug. 

So add the same commands but with internal commands. Click the menu near the add button and select internal commands

---

### Post by Chelidze on 2014-02-11
> **benoitfra said:**
> I've tried (in english now) and it works

Maybe you have added external commands. So it (python) try to launch :
os.system(dictation mode)
that lead to your bug. 

So add the same commands but with internal commands. Click the menu near the add button and select internal commands


I will try to do a clean realinstall and give it a shot

---

### Post by benoitfra on 2014-02-11
Use the pre-release on Github

---

### Post by Chelidze on 2014-02-11
This is what I got (audio is a bit out of sync)

before I recorded this video I managed to write something with voice but could not reproduce that 

[http://ubuntuone.com/4UtWnksKwCbo9Fi7bQHWs2](http://ubuntuone.com/4UtWnksKwCbo9Fi7bQHWs2)

---

### Post by benoitfra on 2014-02-11
AH 

My mistake.

The dictation mode is not a continuous mode so you have to relaunch google2ubuntu with the shortcut for all phrase you want to say. 

As we can see, in the vidéo when there is "done" a /tmp/g2u_dictation should he created (remove it if you not succed to sotp dictation mode)

So say dictation mode to start dictation mode
then relaunch google2ubuntu and say whatever you want
to quit this mode launch google2ubuntu and say the sentence you set to exit

AUDIO was ok mine is worst

---

### Post by Chelidze on 2014-02-11
> **benoitfra said:**
> AH 

My mistake.

The dictation mode is not a continuous mode so you have to relaunch google2ubuntu with the shortcut for all phrase you want to say. 

As we can see, in the vidéo when there is "done" a /tmp/g2u_dictation should he created (remove it if you not succed to sotp dictation mode)

So say dictation mode to start dictation mode
then relaunch google2ubuntu and say whatever you want
to quit this mode launch google2ubuntu and say the sentence you set to exit

AUDIO was ok mine is worst


I updated google2ubuntu from github and now it works thank you :) for the help

Time to personalize it

---

### Post by benoitfra on 2014-02-13
The next release arrive...already on Github and in building on Launchpad.

It will bring:

* Traditional Chinese translation
* Portuguese tranlation
* Setup Window
* A way to set the recording time
* A way to define commands to pause/play the music player

update arrive on ppa

---

### Post by gtx-swift on 2014-11-05
I want to launch/stop dictation mode via keyboard shortcut. Is this possible?

---

