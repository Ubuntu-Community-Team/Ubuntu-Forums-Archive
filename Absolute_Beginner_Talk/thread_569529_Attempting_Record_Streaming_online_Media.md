---
title: "Attempting Record Streaming online Media"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by SpiritIsReality on 2007-10-07
howdy
how  or is it possible to record this stream 
[http://www.tfccs.org/bostonactivities/sundayservice.jhtml;jsessionid=UAJMP1MRFQUODKGL4L2SFEQ](http://www.tfccs.org/bostonactivities/sundayservice.jhtml;jsessionid=UAJMP1MRFQUODKGL4L2SFEQ)
. I can play it if I boot into xp.and click on windows media link. but I don't know how to record it there. the sound recorder only lasts 30 secs. this is about 1\2 hr.
I've got about all the sound packages for sound that ubuntu linux bible talks about for multimedia. how can I check if I've got w32 codecs installed, I think I do.
any way to get any linux program or an altos program in xp to record this. It'd be nice for me to listen to it more than just when they allow it.
please ask me what info to provide. any and all welcomed gratefully hopefully

if I have to just listen to it once that's ok, it's not life and death or anything. It's just something I'd like to be able to do, and then make torrents of it and supply it to the internet if I can get there. thanx in advance.
I've tried to paste the url into totem and vlc . no go. How do you get a wav file when I click on the  link I get a filename but it doesn't play. 
url when click the windows media player listen link is (open in other tab, then read address) [http://boss.streamos.com/wmedia/csps/clerks_office/service/church_service.wvx](http://boss.streamos.com/wmedia/csps/clerks_office/service/church_service.wvx)

  
buds

---

### Post by SpiritIsReality on 2007-10-07
howdy
is this what I'm after?
[http://ubuntuforums.org/showthread.php?t=169278](http://ubuntuforums.org/showthread.php?t=169278)
buds [http://ubuntuforums.org/showthread.php?t=169278](http://ubuntuforums.org/showthread.php?t=169278)
[http://ubuntuforums.org/showthread.php?t=40193&](http://ubuntuforums.org/showthread.php?t=40193&)

---

### Post by n3tfury on 2007-10-07
yes.

---

### Post by SpiritIsReality on 2007-10-07
howdy
thanks
buds

---

### Post by SpiritIsReality on 2007-10-07
howdy
installed realplay from canonical repo and used aptitude.
cuts out after 2or so min of playing. cpu goes to 100% indicated.
audacity- cannot get it to play file .
(guess I got other ways of installing it that might help, or it's what?)
when I get to here I get an error message

fred@p3:~$ vsound &#8211;d &#8211;t &#8211;f myfilename.wav realplay [http://boss.streamos.com/real/csps/clerks_office/service/church_service.smi](http://boss.streamos.com/real/csps/clerks_office/service/church_service.smi)
About to start the application. The output will not be available
until the application exits.
/usr/bin/vsound: 177: &#8211;d: not found
[COLOR=red]Missing file ./vsound18410.au.[/COLOR]
This means that the libvsound wrapper did not work correctlty.
Here are some the possible reasons :
 - You are trying to record a stream (RTSP or PNM protocol) from 
   the internet. You will need to use the --timing option.
 - The program you are trying to run is setuid. You will need to 
   run vsound as root.
 - Vsound was not properly installed and hence won't work at all.

please help
1.the Missing file ./vsound18410.au
I have to do a aptitude search vsound18410.au or how does that go?
I installed vsound  like the guide said, only I used aptitude. from medibuntu repos
apt-file search vsound18410.au returns empty.
try running vsound as root?

2. could you see if you think that's the right url. I sved the .ram file to hard drive and then right clicked and opened with text editor and that's what was there. 

buds

---

### Post by SpiritIsReality on 2007-10-07
I clicked on the realplayer link and chose to open with realplay from /usr/bin
fred@p3:~$ whereis realplay
realplay: /usr/bin/realplay /usr/X11R6/bin/realplay /usr/bin/X11/realplay
and I get the 10 second intro , saying that it will broadcast from 1 eastern sunday till ...sometime monday so I'm waiting till after 10 pdt and I should be good to go?
oh, when realplayer started, it wanted to run thru a startup wizard, did it.

could that be what the error message was about. I didn't start realplayer right when I gave the command 
vsound &#8211;d &#8211;t &#8211;f *myfilename.wav *realplay [I]url_of_the_stream_you_want_to_rip

please ignore this, just stumblin along. haha! had to just click post message to get out of the code box
(what the heck I copied and pasted a code from the web page and I'm trapped in a virtual wt?)
[/I]

---

### Post by SpiritIsReality on 2007-10-07
get this error message still.
fred@p3:~$ vsound &#8211;d &#8211;t &#8211;f myfilename.wav realplay [http://boss.streamos.com/real/csps/clerks_office/service/church_service.smi](http://boss.streamos.com/real/csps/clerks_office/service/church_service.smi)
About to start the application. The output will not be available
until the application exits.
/usr/bin/vsound: 177: &#8211;d: not found
Missing file ./vsound20476.au.
This means that the libvsound wrapper did not work correctlty.
Here are some the possible reasons :
 - You are trying to record a stream (RTSP or PNM protocol) from 
   the internet. You will need to use the --timing option.
 - The program you are trying to run is setuid. You will need to 
   run vsound as root.
 - Vsound was not properly installed and hence won't work at all.

tried with sudo 
fred@p3:~$ sudo vsound &#8211;d &#8211;t &#8211;f myfilename.wav realplay [http://boss.streamos.com/real/csps/clerks_office/service/church_service.smi](http://boss.streamos.com/real/csps/clerks_office/service/church_service.smi)
Password:
About to start the application. The output will not be available
until the application exits.
/usr/bin/vsound: 177: &#8211;d: not found
Missing file ./vsound20558.au.
This means that the libvsound wrapper did not work correctlty.
Here are some the possible reasons :
 - You are trying to record a stream (RTSP or PNM protocol) from 
   the internet. You will need to use the --timing option.
 - The program you are trying to run is setuid. You will need to 
   run vsound as root.
 - Vsound was not properly installed and hence won't work at all.

tried with sudo -i then
fred@p3:~$ sudo -i
root@p3:~# vsound &#8211;d &#8211;t &#8211;f myfilename.wav realplay [http://boss.streamos.com/real/csps/clerks_office/service/church_service.smi](http://boss.streamos.com/real/csps/clerks_office/service/church_service.smi)
About to start the application. The output will not be available
until the application exits.
/usr/bin/vsound: 177: &#8211;d: not found
Missing file ./vsound20660.au.
This means that the libvsound wrapper did not work correctlty.
Here are some the possible reasons :
 - You are trying to record a stream (RTSP or PNM protocol) from 
   the internet. You will need to use the --timing option.
 - The program you are trying to run is setuid. You will need to 
   run vsound as root.
 - Vsound was not properly installed and hence won't work at all.

I have gained ground, thankyou. I can listen to the realplayer file using linux.
It would be nice to record it but I don't know what I'm doing wrong.
but am a lot closer than a hole in the ground at xp. I'll bet there's a mplayer solution to this too, and it
might work just as well as this one. reminds me of my batting average with samba. the net is full of guys 
braggin' up about what a great thing it is and how to do it, but I can't get it to work and don't know why.
back to the cactus. I mean rute ch4.
thanks for any posts that might help, it was fun.
buds

---

### Post by n3tfury on 2007-10-07
i don't rip streaming media for my own reasons, but i remember recording a live podcast under audacity in windows.  it should work the same in ubuntu i would imagine.  sorry i can't help you more than that.

---

### Post by SpiritIsReality on 2007-10-07
wow, that's right thanks pard. I read in the guide about audacity would work. thanks.
thanks for the reminder. .sorry for editing post#7 after your post#8 time. didn't know.

---

### Post by Drakkor on 2007-10-07
I'm getting a 404 not found page now, but before I was able to record it in Ubuntu with
Audacity. it was the 13 second Sunday-Monday promo, which it says starts Sunday 1pm
EST. to Monday sometime.

---

### Post by SpiritIsReality on 2007-10-07
> **Drakkor said:**
> I'm getting a 404 not found page now, but before I was able to record it in Ubuntu with
Audacity. it was the 13 second Sunday-Monday promo, which it says starts Sunday 1pm
EST. to Monday sometime.
could you please explain how you got audacity to play a file because I can't get it.
it won't open the ram file. when I try to get it to open a file with what gedit reads inside the ram file, [http://boss.streamos.com/real/csps/clerks_office/service/church_service.smi](http://boss.streamos.com/real/csps/clerks_office/service/church_service.smi)
says that's a file that contains links to other files, try to open it with gedit and load the actual sound files?
I am not having trouble getting to the site: [http://www.tfccs.org/bostonactivities/sundayservice.jhtml;jsessionid=ZQ030CROUWXXXKGL4L2SFEQ](http://www.tfccs.org/bostonactivities/sundayservice.jhtml;jsessionid=ZQ030CROUWXXXKGL4L2SFEQ)
does this link work for you? or are you just proddin' . (stock prod ... used to cause a shock like a police tazer, to hopefully make the whatever move in the opposite direction to the site of the shock. works on some things better than others. buffalo in point)
buds

---

### Post by Drakkor on 2007-10-07
Actually you don't use Audacity to play it, it will record it however. 
When I click [http://boss.streamos.com/real/csps/clerks_office/service/church_service.smi](http://boss.streamos.com/real/csps/clerks_office/service/church_service.smi)
I get this:, and it's actually played with movie player, or Totem

Do you have Fiesty, and do you have an input selector on Audacity ?

---

### Post by SpiritIsReality on 2007-10-07
> **Drakkor said:**
> Actually you don't use Audacity to play it, it will record it however. 
When I click [http://boss.streamos.com/real/csps/clerks_office/service/church_service.smi](http://boss.streamos.com/real/csps/clerks_office/service/church_service.smi)
I get this:, and it's actually played with movie player, or Totem

Do you have Fiesty, and do you have an input selector on Audacity ? 

OK thanks pard. ya I got tht too.
Thanks for your help. What I did after getting that was to try to get audacity to open the file so that i could try to record it.
Thankyou for your help. What a great place, great people..
wonderful !!! buds

---

### Post by SpiritIsReality on 2007-10-07
Well I can't find movie player  but I can find totem and it just opens it with an error message of cant play...
once I got realplay insalled, it will play the file. but I still don't know how to record it. good stuff though. kind of like samba. a four letter workd in my book so far.
buds

$whereis realplay
$whereis movieplayer
$whereis totem

---

### Post by Drakkor on 2007-10-07
Do you have this ? Click on the screenshot to enlarge

---

### Post by SpiritIsReality on 2007-10-07
howdy
no I surely don't. good for you pard. or are you just real good with graphics?
(missouri hairs standin up on the back of neck)
buds

---

### Post by Drakkor on 2007-10-07
What are you having a problem with ? :)

---

### Post by SpiritIsReality on 2007-10-07
howdy 
this thread just about covers it.
buds

---

### Post by SpiritIsReality on 2007-10-07
```
fred@p3:~$ sudo aptitude remove --purge realplay
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages will be REMOVED:
  realplay 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 15.8MB will be freed.
Writing extended state information... Done
(Reading database ... 140732 files and directories currently installed.)
Removing realplay ...
fred@p3:~$ echo "Install RealPlayer.deb using dkpg
> 
>     *
> 
> 
fred@p3:~$ echo "Install RealPlayer.deb using dpkg"
Install RealPlayer.deb using dpkg
fred@p3:~$ echo "website defunked"
website defunked
fred@p3:~$ echo "I mean defunct"
I mean defunct
fred@p3:~$ Install RealPlayer.deb using dkpg
bash: Install: command not found
fred@p3:~$ 
fred@p3:~$     *
bash: bbcode: command not found
fred@p3:~$ 
fred@p3:~$ 

```

---

### Post by SpiritIsReality on 2007-10-07
installed to Desktop from webpage [http://www.real.com/linux](http://www.real.com/linux) when all said and done there is an executable install file on the Desktop which I've run, but I cant get the realplayer to start, not on menu?
it's real alright, a real pain in the a??.
no solution here for me.try again in Gutsy in a couple weeks maybe.

---

### Post by Drakkor on 2007-10-07
From my recollection, realplayer is a pain in the *** anyway, so you cannot play it in 
Totem ? And record with Audacity ? :confused:

---

### Post by SpiritIsReality on 2007-10-07
> **Drakkor said:**
> From my recollection, realplayer is a pain in the *** anyway, so you cannot play it in 
Totem ? And record with Audacity ? :confused:
I'll give that a try, thanks.

---

### Post by SpiritIsReality on 2007-10-07
> **Drakkor said:**
> Actually you don't use Audacity to play it, it will record it however. 
When I click [http://boss.streamos.com/real/csps/clerks_office/service/church_service.smi](http://boss.streamos.com/real/csps/clerks_office/service/church_service.smi)
I get this:, and it's actually played with movie player, or Totem

Do you have Fiesty, and do you have an input selector on Audacity ?
sorry pard I completely missed your post #12.
I've got Feisty and I will try to open the smi with movie player.when I try to get totem to open the smi url, it gives an error message.

---

### Post by SpiritIsReality on 2007-10-07
please see attachmnet. I have to check Audacity to see if there's an input selector in it.
do you mean File -> open, or ? OK by the manual It's the I in the top left corner of Audacity.
Similar to Cinelerra. oh boy.
Profect -> import audio.

---

### Post by SpiritIsReality on 2007-10-08
When I use the Project, import audio, go to the ram file it gives this message, and I don't know how to get it to open the smi. yet. pointers?

---

### Post by Drakkor on 2007-10-08
Yeah , I don't know how to proceed from here, maybe someone else can chime in. i did however..upgrade to Gutsy this morning, and can now actually record streams because there's an input selector,where as I couldn't record before, and as said before, i just clicked on [http://boss.streamos.com/real/csps/c...ch_service.smi](http://boss.streamos.com/real/csps/c...ch_service.smi)  and selected play in
movieplayer(Totem) and it plays fine, and i can now record it with Audacity !

---

### Post by SpiritIsReality on 2007-10-08
forgot the attchmt herehttp://boss.streamos.com/real/csps/clerks_office/service/church_service.smi
how do you click on the smi url that is open in aa text editor? good question !

---

### Post by SpiritIsReality on 2007-10-08
gutsy time.amen

---

### Post by SpiritIsReality on 2007-10-08
I clicked on the smi link in your last post and I get a 404 not found. I see what you were talkin about.

---

### Post by Drakkor on 2007-10-08
Yeah,lol :) I love challenges,lol :)

---

### Post by Drakkor on 2007-10-08
Yeah, now same 404 ! :lolflag:

---

### Post by SpiritIsReality on 2007-10-08
I'm gettin a feeling that must be that too.love of challenges

---

### Post by SpiritIsReality on 2007-10-08
I'm curious. Did you listen to much of it, and is it any good?

---

### Post by SpiritIsReality on 2007-10-08
I'm gonna boot into xp to have a listen.

---

### Post by Drakkor on 2007-10-08
Actually it's online right now,lol, the only thing I have actually heard is a lot of organ music :)

---

### Post by Drakkor on 2007-10-08
Re: Input Selector ........... in Feisty , I had none, but in Gutsy Gibbon  I have  one........
You need to seperate player,from recorder,e.g Totem and Audacity on the third menu,or toolbar down,in Audacity,you'll see a little speaker with a level control (playback volume), and to the right of it a microphone(record volume), and to the right of that a drorpdown box which allows you to select the input source, for streaming audio, I have selected "Vol", but there of course are other selections. :)

---

### Post by Drakkor on 2007-10-08
I'll pass, isn't it all really pretty subjective ? BTW Carlin rulez,lol :)

---

