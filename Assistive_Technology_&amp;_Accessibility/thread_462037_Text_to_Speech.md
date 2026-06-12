---
title: "Text to Speech"
date: 2007-06-02
forum: Assistive Technology &amp; Accessibility
---

### Post by Robotman on 2007-06-02
Howdy,
I just installed Ubuntu 7.04 and I really like it, especially its speed compared to XP.  Unfortunately, I can't seem to get any text to speech software to work yet.  If I could get a speech synthesiser to read text for me like I can with windows (using "TextAloud MP3"), I could abandon that other OS altogether, as 'reading' news is what I do most with this PC.
Is there any good text-to-speech software that will run in Ubuntu?  I've read about and downloaded something called "Festival" but I don't know what to do with all those files and I've read that it doesn't have a GUI.  Any tips to have me listening to my text would be very welcome. ;)

---

### Post by frafu on 2007-06-02
Ubuntu Feisty ships with a screenreader named Orca. 

Have a look at the menu System->Preferencs->Accessibility->Assistive Technology Preferences.

That might help you. 

Francesco

---

### Post by Robotman on 2007-06-02
Thanks.  That's a great start... but ideally I want something that only reads what I tell it to read, not every window that comes to the foreground.

---

### Post by joann on 2007-06-09
I am visually impaired and often find it nice to have software read for me as an addition to my screen magnification software. So I do understand the desire to have software that will read what I tell it to read.

There are several programs that may help you :)

Here is a small list of useful programs and add-ons. The links have more details about the programs and how to install them...

_Emacspeak-_ this is a talking extension to the emacs editor
<http://emacspeak.sourceforge.net/>
   This can be installed easily using the synaptic package manager or 'apt-get install emacspeak'. but make sure that all of the dependencies are satisfied prior to installing emacspeak other wise it will not function properly.
_KTTS-_ KDE text to speech system
     This works well with KDE, and allows items on the clipboard to be spoken.
   <http://accessibility.kde.org/developer/kttsd/>
   I think this should be installed by default, maybe. But if it not, you can install it using synaptic package manager. The website will have a more information.
 
_Read Out Loud-_ This is for the Adobe PDF reader, it allows for pdfs to be spoken. Very nice when you just want to listen to a PDF document.
        This link has information on how to set up Read Out Loud
	<http://help.adobe.com/en_US/Acrobat/8.0/Standard/help.html?content=WS58a04a822e3e50102bd615109794195ff-7d15.html>
        And this link has the software ...
        <http://www.adobe.com/products/reader/>

_ClickSpeak-_ This is an exension for firefox. It will speak web pages for you, and highlight the text while it reads. (I realy like this alot! It can also be used with or without Orca for speech which is realy nifty)
   <http://clickspeak.clcworld.net/>
   Click on installation guide, and follow the directions to install the extension.

Hope that you find this useful.
Have a wonderful day.

-Joann

---

### Post by Robotman on 2007-06-10
Thanks for the info Joann. ;)  I think KTTSD (along with KTTSMGR and KSAYIT) are exactly what I'm looking for... but I can't figure out for the life of me how to install KTTSD or Festival or its voices.  What am I missing?

---

### Post by joann on 2007-06-10
Robotman,

Lets see the easiest way to check is to see what software you have installed. So, if you open synaptic package manager, and do a quick search for "speech" a whole bunch of neat stuff should appear off to the upper left hand corner with a description in the lower left portion of the window. If you scroll through the list, at around the letter K you should see kmouth, ksayit, and kttsd. Make sure these have all been checked. Also, at around the letter F there should be festival too, so make sure it is installed as well. 

The search results should list a bunch of goodies, including other speech synthesis software which will produce other voices. You may find these useful ... "eflite", "espeak", "flite". (Commercial software is also available to provide even more voices).

After apply the changes and installing the software you should be able to open KTTSD, by going to Applications->Accesbility->kttsmgr. First  K you should see kmouth, ksayit, and kttsd. Make sure these have all been checked. Also, at around the letter F there should be festival too, so make sure it is installed as well. 

Hope that this helps :)
- Joann

---

### Post by Robotman on 2007-06-11
Thanks Joann, that worked. :D

---

### Post by TheDro on 2008-05-09
Here's a quick question about this. Will this work even though I am using gnome and not kde. In a more general sense, can I install any kde program in the add/remove program list or do I actually have to install the whole kde desktop (probably not the right term) to be able to use these programs?

Btw, I realize that many of you probably think I should just install it, try it out and uninstall it if it doesn't work but I have dial-up and downloading is slow:(.

---

### Post by unutbu on 2008-05-09
If you type 

```
sudo apt-get --simulate install kttsd
```
you'll get to see which packages will be installed.

If you type
```
sudo apt-get install kttsd
```
you'll be told how many MB of space the packages will consume, and you'll be asked if you want to do this. (Note, if kttsd is the only package that needs to be downloaded, then you won't be asked. Only if there are dependencies that need to be downloaded first.)

---

### Post by Hydrosis on 2010-02-15
> **xzcallaway said:**
> The Ubuntu Text Reader can read any text that you paste into it and you can customize it with different voices.

You can download the latest version at:

[http://xzcallaway.synthasite.com/](http://xzcallaway.synthasite.com/)

This is exactly what I've been looking for.  I always wonder why so many Linux apps just don't work out-of-the-box and have simple GUIs, like KTTS/Kmouth and Festival.

This should be integrated into the next Ubuntu as a default app.  Its small and very, very useful.

---

### Post by phillw on 2010-02-17
> **Hydrosis said:**
> This is exactly what I've been looking for.  I always wonder why so many Linux apps just don't work out-of-the-box and have simple GUIs, like KTTS/Kmouth and Festival.

This should be integrated into the next Ubuntu as a default app.  Its small and very, very useful.

Also there is a GUI for espeak in the repo' for 10.04  It is simply called espeak-gui - It reports a couple of errors reported on launch (the author is looking into them) but works fine with either pasted text, or opening a text document

Regards,

Phill.

---

### Post by go_beep_yourself on 2010-02-17
> **joann said:**
> I am visually impaired and often find it nice to have software read for me as an addition to my screen magnification software. So I do understand the desire to have software that will read what I tell it to read.

...

_KTTS-_ KDE text to speech system
     This works well with KDE, and allows items on the clipboard to be spoken.
   <http://accessibility.kde.org/developer/kttsd/>
   I think this should be installed by default, maybe. But if it not, you can install it using synaptic package manager. The website will have a more information.

Does this have an option to automatically read clipboard contents like 2nd Speech Center and TextAloud in Windows? Have you tested this with Gnome?
 
> _Read Out Loud-_ This is for the Adobe PDF reader, it allows for pdfs to be spoken. Very nice when you just want to listen to a PDF document.
        This link has information on how to set up Read Out Loud
    <http://help.adobe.com/en_US/Acrobat/8.0/Standard/help.html?content=WS58a04a822e3e50102bd615109794195ff-7d15.html>
        And this link has the software ...
        <http://www.adobe.com/products/reader/>

I've gotten this to work in Windows. I thought the Linux version of Adobe Reader just left this feature not implemented. I just searched the link you provided. Nothing comes up when doing a search on that site for linux. I am fairly sure I've tried to use this feature in Linux before a while back, and it was "greyed out" where I couldn't click on it.

I've gotten very used to having TTS software such as 2nd Speech Center and TextAloud in Windows, and it's been a real pain in the butt not to have something as functional in Linux. I started the development of a Open Source TTS software written in Java that will use existing tts engines such as festival and espeak. I've made progress on it. Although some features are unimplemented, I will put it up on Google Code, if anyone is interested in it, and I've made some progress so far. I hope to find some coders interested in developing this software too. I've got great plans for it. I just need to implement the rest of the features, but so far, I've gotten through some hurdles.

---

### Post by LequidMetal on 2010-02-28
I tried getting the Read out loud feature to work in Ubuntu and was completely unsuccessful . Orca works with every other app including firefox but for some reason it wont work with Adobe acrobat 9 (or any other gnome pdf readers i tried ).And there seems to be very few tutorials on the subject .

---

### Post by notlistening on 2010-03-01
There is a little application called pdf2txt which when run on a pdf will put its written contents into a text file which in turn can then be very easily read with any TTS program or orca.

---

### Post by go_beep_yourself on 2010-03-18
For anybody interested in seeing an open source application similar to TextAloud and 2nd Speech Center (Windows apps) further developed, I could use some help with this project. So far, it has just been me working on it. I am trying to understand how espeak and mbrola work together, though if easier or better, I would develop this program to use festival or flite. I do not see many command line options for those apps and sence my program runs espeak with arguments gathered from the gui, I don't see the others as an option. My application is working. So far it is able to take any text highlighted and copied, and if what is highlighted is text and is different, the text is read by espeak with the default voice for horrible default espeak voice, so I am trying to understand better how espeak and mbrola work together to get some better sounding voices for this application to use. If anyones interested in seeing this project grow, please contribute whether you know how to program in Java or not, you can still contribute by trying the application and helping me to figure out how different features are used through the command line, so they can be put into the application or by packaging it as debs.

Edit: This app allows anything that can be copied as text to the clipboard to automatically be read to you whether the text is in  Firefox, pdfs, email, etc.

---

### Post by notlistening on 2010-03-18
I am glad to see someone making the effort to develop tools like this. I wrote a similar tools for windows back in the day when i knew what windows was.

I think the direction you want to go is to start looking at speech dispatcher. This creates a single interface into all the most commonly used speech engines. So you only have to learn about speech dispatcher not all the different TTS engines. If better text to speech is what you want then I can recommend my project open-sapi which allows Linux users to use Windows based TTS with much nicer voices. It is under development but I have very kindly added in a command line interface for it which is quite straight forward.

The wiki information is quite out of date and there is a hidden development branch that has taken on new features and got quite a lot of bug fixes. So if you're online on irc MSN skype and your interested then let me know.

---

### Post by 2hot6ft2 on 2010-03-18
> **go_beep_yourself said:**
> I am trying to understand how espeak and mbrola work together, though if easier or better, I would develop this program to use festival or flite.
You might take a look at Gespeaker it' a front end to espeek and uses Mbrola add ons which are a bit more tolerable and it has some controls for how they are managed along with a decent GUI. Sorry but I have no programming knowledge to help with anything.
Here's the home page for it.
[http://code.google.com/p/gespeaker/](http://code.google.com/p/gespeaker/)

---

### Post by hellocatfood on 2010-03-23
> **2hot6ft2 said:**
> You might take a look at Gespeaker it' a front end to espeek and uses Mbrola add ons which are a bit more tolerable and it has some controls for how they are managed along with a decent GUI. Sorry but I have no programming knowledge to help with anything.
Here's the home page for it.
[http://code.google.com/p/gespeaker/](http://code.google.com/p/gespeaker/)

Thanks for that! It's the best/easiest one that I've used so far

---

### Post by go_beep_yourself on 2010-03-23
> **2hot6ft2 said:**
> You might take a look at Gespeaker it' a front end to espeek and uses Mbrola add ons which are a bit more tolerable and it has some controls for how they are managed along with a decent GUI. Sorry but I have no programming knowledge to help with anything.
Here's the home page for it.
[http://code.google.com/p/gespeaker/](http://code.google.com/p/gespeaker/)

I have gespeaker, and although it is a nice app, it does not do what I want. I don't need any coding help. What I need help is to understand how mbrola and espeaker work together, so I can further develop the application I have.

I was about to continue developing my Text To Speech software some more, and have it use mbrola voices.

I looked at the documentation here.

file:///usr/share/doc/espeak/mbrola.html (note: you can open this in Firefox by pasting the above line in FF's address bar)

And it says

"The Mbrola voices are cost-free but are not open source. They are available from the Mbrola website at:
[http://www.tcts.fpms.ac.be/synthesis/mbrola/mbrcopybin.html](http://www.tcts.fpms.ac.be/synthesis/mbrola/mbrcopybin.html)"

So I go to that website, and there are many downloads listed. I'd like to know what the differences are and what each download is for.

From the website:

# LINUX i386 / ppc / alpha / ultra1                           <-- these I am not certain about
# LINUX / Pocket PC                                              <-- This must be for a PDA running Linux
# LINUX / Ircha / Mbrola / ES1 DBA / Z80                <-- I don't know what the different downloads here are for, but I'd like to know
                                                                               what each are. They may all be beneficial to the program I am creating.
# AMD64/Linux                                                      <-- this one is obviously for Linux users running a 64-bit kernel
# ARM/Linux (tested on Nokia N800 and N810)         <-- this one is obvious it runs on cell phones

Could someone please explain what the difference between these download are and what the ones I am not sure about do? It's not the programming I am stuck on. It is things like this that I must understand in order to further the program, and I want it my program to be able to used by others, not just myself.

---

### Post by VastOne on 2010-03-24
> **2hot6ft2 said:**
> You might take a look at Gespeaker it' a front end to espeek and uses Mbrola add ons which are a bit more tolerable and it has some controls for how they are managed along with a decent GUI. Sorry but I have no programming knowledge to help with anything.
Here's the home page for it.
[http://code.google.com/p/gespeaker/](http://code.google.com/p/gespeaker/)

I followed the gespeaker instructions to a T and successfully installed both it and Mbrola.

But where is it? I have no starting app icon anywhere and running gespeaker or Gespeaker from terminal gives me nothing???

Any help appreciated!

---

### Post by go_beep_yourself on 2010-03-24
> **VastOne said:**
> I followed the gespeaker instructions to a T and successfully installed both it and Mbrola.

But where is it? I have no starting app icon anywhere and running gespeaker or Gespeaker from terminal gives me nothing???

Any help appreciated!

dpkg -L gespeaker

---

### Post by Talorgan on 2010-04-16
Is there such a thing as text-to-dialogue software?

The idea would be that the computer would give the different characters of a play different voices so that you could hear the conversation.

---

### Post by notlistening on 2010-04-18
Umm not sure for other TTS engines but SAPI / opensapi can be used with speech XML where you can define how the speech engine processes the speech throughout a document. So you can define different voices / pitch / speech/volume for different parts in theory. Other engines might support similar facilities. 

NL

---

### Post by hellocatfood on 2010-04-19
Another one to look out for is [Simon](http://simon-listens.org/index.php?id=122&L=1). It's only for newer versions of KDE though...

---

### Post by Talorgan on 2010-04-22
Thanks

I'll check these out

---

### Post by culturegeek on 2010-05-02
Wrong thread. Apologies.

---

### Post by wesselvanpersie on 2010-06-08
Does there exist some free text to speech software which uses Unit selection  synthesis?
So using a large database  of recorded speech to make new speech.

I think both eSpeak and geSpeaker use  Diphone synthesis. Which uses only a small dataset of bi phones. While these programs are small, they tend to sound robot like.
Like this:
[http://www.youtube.com/watch?v=M5Z2YGV2CJ0](http://www.youtube.com/watch?v=M5Z2YGV2CJ0)

The current state of the art of text to speech is so much better then this :-/!

---

### Post by wesselvanpersie on 2010-06-19
> **induswebi said:**
> It was the nice speech to read about.

[Dynamic Web Design]("http://www.induswebi.com"), [Web Designing Company]("http://www.induswebi.com")
[Website Designing India]("http://www.induswebi.com"), [Website Designing Company]("http://www.induswebi.com")
[Web Promotion Company]("http://www.induswebi.com/web-promotions.php"), [ Web Development India]("http://www.induswebi.com")
[ SEO Company India]("http://www.induswebi.com/professional-advanced-google-search-engine-optimisation.php"), [ SEO Service India]("http://www.induswebi.com/professional-advanced-google-search-engine-optimisation.php")


Is this spam?

---

### Post by Elfy on 2010-06-20
> **wesselvanpersie said:**
> Is this spam?

it was

---

### Post by vangop on 2010-06-24
Hey guys!
I'm too used to having nice TTS that I can't accept festival/espeak on linux. They sound too much like "microsoft Sam default voooooice" :) and non-english languages are unacceptable.
I have great nextup/acapela voices which worked great out of the box in Win with coolreader book reading app and few others as well.
In 10.04 ubuntu I can't install them under wine. 
Coolreader works fine.
Acapela license manager simply doesn't see the license (reported in wine appdb), and nextup voice is not visible by coolreader. It must have been incorrectly registered in wine registry or something.
Was anyone able to install/use commercial win sapi voices in ubuntu?

---

### Post by notlistening on 2010-06-25
> Was anyone able to install/use commercial win sapi voices in ubuntu?

Yeah I am, using various SAPI Speech engines. I have not tested all of them though. You might want to pm me and have a read of:

[http://code.google.com/p/open-sapi/](http://code.google.com/p/open-sapi/)

Please bear in mind that it's still under heavy development. 

NL

---

### Post by wesselvanpersie on 2010-07-06
Could you report your findings?

I'm looking for a good English text to speech application, better then eSpeak.

I guess I'm willing to pay money for it.

But preferably I would like to use some open source software, so I can make modifications myself.

As I said earlier, not all text to speech applications work in the same way.
These formant based synthesis / di-phone synthesis applications like eSpeak make it really fatiguing to listen to it for more then 5 minutes.

Unit selection synthesis applications take up a thousand times more disk space, but I find them much nicer to listen to.

---

### Post by vangop on 2010-07-07
sapi voices work fine on wine. I'm using next-up voices over wine. They are commercial though. I didn't manage to install acapela voices, its license manager won't see the trial license so I couldn't try it, but people report it is better.
I spent a day trying to debug the stupid licman with strace to see why it doesn't see the files, but still no luck.
I didn't find a way to read web pages with text aloud so I removed the stupid thing :). I use coolreader2 to read books I download.

---

### Post by notlistening on 2010-07-08
Can people list the voices they have working with wine please just out of intrest and those that don't.

I have the basic MS voices:
Sam
Mike 
Mary
The newer MS Vista/7 voice Anna

VoiceWare Kate16k
VoiceWare Paul16k
VoiceWare Julie

Can people add to the list as they try good and bad ones please. 

NL

---

### Post by vangop on 2010-07-09
I've tried Loquendo voices, all work fine, NextUP voices (Katerina), no problem as well. 
I failed to install (not run) Acapela due to the stupid license manager which doesn't see the license.
IMHO as long as you can install a voice engine, you will have it working OK.

---

### Post by wesselvanpersie on 2010-08-04
Do these voices sound as crappy as this?
The intonation is just so terrible.
The pitch goes up and down where its not supposed to go up or down.

[http://www.innoetics.com/media/tts_iandemo_en.mp3](http://www.innoetics.com/media/tts_iandemo_en.mp3)

here is an online demo which allows you to input your own words:
[http://www.acapela-group.com/text-to-speech-interactive-demo.html](http://www.acapela-group.com/text-to-speech-interactive-demo.html)

---

### Post by kline on 2010-12-11
> **Talorgan said:**
> Is there such a thing as text-to-dialogue software?

The idea would be that the computer would give the different characters of a play different voices so that you could hear the conversation.

The "festival" suite that was started by Prof Alan Black and many others over in Edinburgh is worth looking at.  If you google up "festival, tts"
you'll find truckloads of material.  It is the most complete TTS around.

---

### Post by vangop on 2010-12-20
I was too optimistic saying that SAPI installs just fine. If you install it with default settings, the voices might be messed up/not registered properly.
Found some workarounds and tried to outline it [http://ubuntu-answers.blogspot.com/2010/12/text-to-speach-sapi-on-linux-ubuntu.html]("http://ubuntu-answers.blogspot.com/2010/12/text-to-speach-sapi-on-linux-ubuntu.html")

---

### Post by Talorgan on 2010-12-20
> **kline said:**
> The "festival" suite that was started by Prof Alan Black and many others over in Edinburgh is worth looking at.

Thanks!

I'll take a look.

Presumably seeking "text-to-play" software is just a bit optimistic at the moment?!

("Play" as in "theatre production")

---

### Post by notlistening on 2010-12-21
Yes I have been using/developing using comercial windows TTS engines under linux. Things have growned to a halt due to a new very demanding job and no other help on the project. The key to getting it all to work is in wine setting the default OS to windows 2000 and then installing the SAPI installer. You can find a quick way to do all thing here: [http://code.google.com/p/open-sapi/wiki/DeveloperEnvironment]("http://code.google.com/p/open-sapi/wiki/DeveloperEnvironment")

This will get you up and running using the Neospeech voices at least. I can not speak for others but generally you can get them working with a bit of work.

Drop me a message if you need further help.

---

### Post by LewRockwellFAN on 2011-01-25
NextUp and Loquendo both work fine in Wine. And both sound great. Under NextUp you can install the Ivona voice.* You'll have to google around a bit for the exact procedure on the NextUp as it is a bit tricky. If I recall you install it in Wine emulating one variety of windows and run it under another variety or something like that.  I've done it and it worked fine and Ivona is a great voice. But that was a natty installation I've since junked for other reasons and it was a free trial on the NextUp anyway. A friend of mine has the Loquendo running under wine and several voices and he can make it do tricks. Sounds good.

*I wasn't quite right about that. See later post in this thread.

---

### Post by LewRockwellFAN on 2011-01-25
One more thought, [xzcallaway]("http://ubuntuforums.org/member.php?u=648712"), I truly mean no offense and your site looks interesting, but why should anyone install a deb from someone they know nothing about? It's not like getting it straight from some well known project or compiling source you have written yourself. It seems to be a major security breach potentially. If you can explain why I am wrong about this I would be glad to hear it. Seriously, I'm sure your debs are fine, but isn't this a pretty bad practice? I may be totally offbase on this and if so, I'd appreciate being educated. But it seems contrary to what I understand as the common perception of secure procedure. Maybe it's acceptable to just scan them with clam or something. I'd appreciate informed comment on this point.

---

### Post by budix on 2011-02-24
What youre saying is completely true... I know that everybody must say the same thing, but I just think that you put it in a way that everyone can understand[.]("http://www.aatma.org")...I also love the images you put in here... They fit so well with what youre trying to say... Im sure youll reach so many people with what youve got to say...

---

### Post by LewRockwellFAN on 2011-04-04
Since my previous post in this thread, I've experimented with TTS again and I need to correct one mistatement. While I have been able to get the Ivona voices working on a free trial they do NOT continue to work for me after the next reboot. Despite the fact the trial is supposed to be for 30 days, the liscences expire as soon as I reboot. I didn't realise this the first time I tried them cause the Natty installation screwed up hopelessly on reboot and I had to reinstall. Installing Ivona takes a loooooooooooooooooooooooooong time so I'm not going to experiment with it any more unless I have some reason to think that problem is fixed. Way too much work to go to just on the chance you might be able to get it right with another try. I tried under both versions of Wine in the repository. A VirtualBox or similar VM with Windows in it might work, but it takes at least XP and the only Windows I have been able to install in VirtualBox is 2000. I tried a W7 trial disk but VirtualBox  fails to install it giving an erroneous low disk space on host error message and I haven't been able to figure out Faubox. Darn things sound great though. If anyone gets a trial to work I'd like to hear about how they did it. But I'm sure not going to buy it without getting the trial to work cause the licsensed version might have the same problem.

---

### Post by zoubidoo on 2011-12-30
Lucid LTS + Virtualbox + WinXP + Ivona trial version works perfectly.  Just make sure you give the VM plenty of disk space.

I'd be uncomfortable paying for it as it needs virtualbox and windows.  But if it could be installed thought the ubuntu software centre, I wouldn't hesitate for a moment.

---

### Post by Dreamer Fithp Apprentice on 2012-01-20
I have tried to get Ivona to work also. Never had any luck with Wine at all. In a Virtualbox with XP I can get the British voices to install and the American voices down to Salli ("down to" that is, in terms of the order in which they are listed in the installer, which is NOT alphabetical) but neither Salli nor any of the American or non-english voices past Salli would install. I don't think it is just disk space because I tried installing JUST Salli and it wouldn't work.  I don't think it is a case of older voices work and newer ones don't because I think Ewa was their first voice and it is one of the ones that won't install. Go figger.

---

### Post by Michal Fapso on 2012-01-30
Here is a Perl script which takes a text file as input and generates mp3 file. It uses Google TTS:

[http://michalfapso.blogspot.com/2012/01/using-google-text-to-speech.html](http://michalfapso.blogspot.com/2012/01/using-google-text-to-speech.html)

---

### Post by frytek on 2012-02-06
> **Michal Fapso said:**
> Here is a Perl script which takes a text file as input and generates mp3 file. It uses Google TTS:

[http://michalfapso.blogspot.com/2012/01/using-google-text-to-speech.html](http://michalfapso.blogspot.com/2012/01/using-google-text-to-speech.html)

I wonder when Google guys realize they need captcha there. :)


BTW: anybody could use this script create a new one which would do the same using Android SVOX pico2wav? SVOX has a nice voice and runs on Ubuntu, but it accepts only very short strings. Basically, we would need splitting the text and sending it phrase by phrase in the same way. I am only a user and I can't do it myself. :(

---

### Post by majster on 2012-02-15
I absolutely LOVE this script !!!! :guitar::guitar::guitar:=D>

THANK YOU MICHAL FAPŠO :)

---

### Post by Dreamer Fithp Apprentice on 2012-02-26
> **frytek said:**
>  . . . SVOX has a nice voice and runs on Ubuntu . . . 

Would somebody who understands that mind clarifying it? I find some SVOX libs in synaptic but it isn't at all clear what I'm to do with them.

---

### Post by go_beep_yourself on 2012-05-09
I think I know exactly what you are looking for. Check the youtube video that's on this blog for the software JSpeak.

[http://linuxinnovations.blogspot.com/2012/05/jspeak-ultimate-in-linux-text-to-speach.html](http://linuxinnovations.blogspot.com/2012/05/jspeak-ultimate-in-linux-text-to-speach.html)

---

### Post by Ter Rymon on 2012-11-09
I use gespeaker 0.8.1 and added the following as a keyboard shortcut (Super+R)

Name: 
Read Text
Command:
bash -c "gespeaker --play-text=\"$(xsel | sed -e :a -e '$!N;s/\n/ /;ta')\""

gespeaker and xsel need to be installed prior

sudo apt-get install gespeaker xsel

Edit: You need to get the latest deb file for gespeaker at code.google.com/p/gespeaker/downloads/list

---

### Post by NewAmercnClasic on 2012-11-13
> **Hydrosis said:**
> This is exactly what I've been looking for.  I always wonder why so many Linux apps just don't work out-of-the-box and have simple GUIs, like KTTS/Kmouth and Festival.

This should be integrated into the next Ubuntu as a default app.  Its small and very, very useful.

 I agree.

---

### Post by honeybear on 2012-12-04
> **Robotman said:**
> Howdy,
I just installed Ubuntu 7.04 and I really like it, especially its speed compared to XP.  Unfortunately, I can't seem to get any text to speech software to work yet.  If I could get a speech synthesiser to read text for me like I can with windows (using "TextAloud MP3"), I could abandon that other OS altogether, as 'reading' news is what I do most with this PC.
Is there any good text-to-speech software that will run in Ubuntu?  I've read about and downloaded something called "Festival" but I don't know what to do with all those files and I've read that it doesn't have a GUI.  Any tips to have me listening to my text would be very welcome. ;)

I can code for you many things using festival. 

I pilot a computer over irda, and festival does the rest. I use a bit of speech recognition when I am alone in office and home.

PM me if you would like help.

---

### Post by honeybear on 2012-12-04
> **zoubidoo said:**
> Lucid LTS + Virtualbox + WinXP + Ivona trial version works perfectly.  Just make sure you give the VM plenty of disk space.

I'd be uncomfortable paying for it as it needs virtualbox and windows.  But if it could be installed thought the ubuntu software centre, I wouldn't hesitate for a moment.

Not bad. I have found this script. It works for me for few words. 

```

#!/bin/sh


ProcFestival() {
  if [ "$1" = "--festival" ]   ; then 
    echo "$2" | festival --tts
  fi
}

ProcIncreaseMic() {
  amixer -q -c $VALMIC   set 'Mic',1 100%
  amixer -q -c $VALMIC   set 'Mic',0 100%
}

ProcMic() {
  if  [ "$1" = "--checkmic" ] ||  [ "$1" = "--mic" ]  ||  [ "$1" = "--hwmic" ] ; then
    CARDNBR=` arecord -l | grep "^card "  | sed 's/://g' | awk ' { print $2 }  '  `
    [ "$2" = "--debug" ] && echo "$CARDNBR"
    if [ "$1" = "--mic"  ] ||  [ "$1" = "--checkmic"  ] ; then 
      [ "$2" != "" ]  && CHMIC=` echo "$CARDNBR" | grep $2  ` 
      if [ "$CHMIC" = "" ] ; then 
        VALMIC=` echo "$CARDNBR" | tail -n 1 `
        ProcIncreaseMic
        echo "$VALMIC"
      else
        VALMIC="$2"
        ProcIncreaseMic
        echo "$VALMIC"
      fi
    fi 
  fi
}

if [ "$1" = "custom" ] ; then 
  mkdir -p $HOME/tmp/custom 
  wget http://pastebin.ca/raw/2199967  -O $HOME/tmp/custom/sample.dfa
  wget http://pastebin.ca/raw/2199968 -O $HOME/tmp/custom/sample.dict
  wget http://pastebin.ca/raw/2199969 -O $HOME/tmp/julian-custom.jconf
  echo "Custom fetched and done"
  exit
fi

if [ "$1" = "install" ] ; then 
  mkdir -p $HOME/tmp/ 
  cd $HOME/tmp 
  if [ ! -f  Julius-3.5.2-Quickstart-Linux_AcousticModel-2011-07-21.tgz ] ; then
    wget http://www.repository.voxforge1.org/downloads/Nightly_Builds/AcousticModel-2011-07-21/Julius-3.5.2-Quickstart-Linux_AcousticModel-2011-07-21.tgz  -O  Julius-3.5.2-Quickstart-Linux_AcousticModel-2011-07-21.tgz
  fi 
  tar xvpfz Julius-3.5.2-Quickstart-Linux_AcousticModel-2011-07-21.tgz 
  echo "It might be installed."
  exit
fi


if [ "$1" = "voc" ] ; then 
  cd 
  cd tmp
  cd bin
  vim sample.voca
  ./mkdfa.pl sample
  exit
fi


FETCHMIC=` ProcMic --mic "$2"  `
echo "Fetchmic : $FETCHMIC"
AUDIODEV=` echo  "/dev/dsp${FETCHMIC}" | awk ' {gsub("dsp0","dsp") ; print $0  }   '`
export AUDIODEV ;  echo  $AUDIODEV  
counter=1

cd
cd  tmp

if  [ ! -f julian-custom.jconf ] ; then 
  echo "custom/julian.jconf not found"
  echo "Please run-it with custom or install"
  exit
fi


./julian -demo -input mic -C julian-custom.jconf | while read -r  i ; do 

if [ $counter -eq 130 ] || [ $counter -eq 129 ] ; then
  echo "** READY * Please Speak **"
fi

if [ $counter -ge 129 ] ; then
  echo "**$counter** $i **"


  CHPAS=` echo "$i" | grep "sentence1: <s>" `
  echo "CHPAS $CHPAS" 
  if [ "$CHPAS" != ""  ]  ; then 
    echo "FOUND CHPAS $CHPAS" 
    FOUND=""
    FOUND=`echo "$i" | awk ' { print $3  }    '`
    ProcFestival --festival "$FOUND"


    if [ "$LAST" != "ZERO" ]   &&  [ "$FOUND" = "ZERO" ]   ; then 
      ProcFestival --festival "The Command is $FOUND"

      # here add whatever you would like linux to do ...
      [ "$LAST" = "ONE" ]   && xterm &
      [ "$LAST" = "TWO" ]   && audacious &
      [ "$LAST" = "THREE" ]   && xclock &
      [ "$LAST" = "NINE" ]   && date | festival  --tts &
      # ...
    fi
    LAST="$FOUND"
  fi 
fi

counter=$(( $counter +1))
done
```

---

### Post by go_beep_yourself on 2012-12-14
[https://github.com/BullShark/JSpeak](https://github.com/BullShark/JSpeak)

---

### Post by BradDear on 2013-04-14
In gespeaker, is there a script that allows you to modify the common words and contractions (such as e.g. = for example, i.e. = that is, etc = et cetera)?

I've been looking for this in the source code, but I can't seem to find it.

---

