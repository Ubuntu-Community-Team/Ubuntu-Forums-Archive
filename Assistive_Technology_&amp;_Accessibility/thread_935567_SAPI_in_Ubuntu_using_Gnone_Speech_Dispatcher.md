---
title: "SAPI in Ubuntu using Gnone Speech Dispatcher"
date: 2008-10-01
forum: Assistive Technology &amp; Accessibility
---

### Post by notlistening on 2008-10-01
Hi Everyone,


I have been considering a project for sometime now and have finallly freed enough time to begin working on it. It is really a quick hack to get the MS SAPI speech engines to work under Linux not just Ubuntu. 

I have SAPI running under WINE *Note that Hardy breaks the install process of the MS SAPI 5.1 SDK. I have hacked that around a bit and got it working again but by default it does not work. I have submitted a bug report to the WINE team. 

I also have VWKate SAPI 5 from NeoSpeech installed. This has been tested using the TextAloud package and also the MS examples under WINE. 

From there I am in the process of writing an executable in windows that implements the basics of the SAPI engine and Gnone Speech Dispatcher interfaces.

To increase the speed of development (in theory ;) ) I have used tcl to script the SAPI to Speech Dispatcher middle ware. This is using a combination of TCOM for windows com objects into the SAPI engine. Speech Dispatcher uses standard in and out for communication.

This will create a Server Client Model onto the SAPI engine that can allow for communications from Linux based programs and software to call the SAPI engine to speak.  

So I think it is possible to get this functioning and I am interested to know from people here:

Firstly if people can get over the fact that i am using MS on Linux. ;)

Secondly if there is anyone with any suggestions, that wants to help out, that have a particular interested to see this working. Please drop ne a message or post on this thread.

Tom

---

### Post by doviende on 2008-10-05
Yes!  I will worship the ground you walk on if i can use SAPI5 voices in linux.  I haven't yet figured out how to do this...i tried installing textaloud in wine but it can't see the sapi5 voices i have, so i'm stuck.

i was considering running windows in vmware to try to make this work because i desperately need it right now.

---

### Post by notlistening on 2008-10-27
Proof of concept it works! Hopefully we will see SAPI on Ubuntu soon. 

I now have an executable that speaks using SAPI using wine and the basic Microsoft default speech engine. I have also installed an additional speech engine from NeoSpeech VWKate and once selected it will use any installed speech engine.

Main Tasks:
1. Speech Dispatcher SAPI driver
2. SAPI Installation & Config
3. Middleware
4. Package   

 ToDo Breakdown:
1. Create stdin file event handeler - Not Started
2. Create dispatch code for stdout - Not Started
3. Rate, volume, voice, sound device - In Progress
4. Event reporting - Researchig
5. Read SPI specification - Researching
6. Create aware network enabled option - In Progress
7. Intergrate tcom into standalone executable - Done
 7a. Create install for C++ library to /system32 - Not Started
8. Install SAPI on Ubuntu - Broken but Jimmied - In Progress
 8a. Create standalone installation package - Not Started
 8b. Identify and generate filelist - In Progress
 8c. Identify SAPI registry entries & Reproduce - In Progress 
9. Test SAPI 4/5 Install Packages - 4 Tested
  - Default MS Engine SDK5.1 - Working
  - VWKate Neospeech - Working	 

Any help still welcomed, especially testers :)

Tom

---

### Post by Ohmu on 2008-11-06
WOW.
W O W
Tom, You're a legend!  This is incredible!  Amazing!

I'm just looking at doing exactly the same thing, Was getting desperate.  Then I see your post!

I'm pushing to get a wholly FOSS speech engine+GUI.

I blogged the start:

[http://womblezone.blogspot.com/]("http://womblezone.blogspot.com/")

<exerpt>
[INDENT]The plan

   1. Use WINE to get Vista's Speech Engine operating in Linux
   2. Create a GUI that'll interface with this engine.
      The GUI will sporadically (unless the user disables the feature) send phrase-data to a central database (say VoxForge - I have contacted the maintainer and he is friendly)
   3. Once we have enough data, throw out the WINE-wrapped Vista Engine, and replace it with our own FOSS engine.
[/INDENT]

Please have a look and tell me what you think!

hmm SAPI 5.1 doesn't have a UK english voicemodel.  This is why I was trying to port the Vista one, but it's possibly horribly embedded.  Anyway, I'm well up for learning American, in order to write my emails.

I hope we can meet up on the internet (I'm in India now) and chat!  How about irc.freenode.net#cmusphinx?

Let's do it!  Let's get a SAPI engine in Linux, and seed a FOSS GUI that kicks Vista Speech Assistant's bony butt!

Sam

---

### Post by Ohmu on 2008-11-14
Quick update,

I'm now running Vista + Visual Studio in VirtualBox

I'm using the SimpleDictation sample from the Windows SDK

...compiling a release build and trying to port this to Wine.  It's the simplest possible way to test that SAPI 5.3 has transferred over ok.

I think there's a good chance of this working... I'll post another update in a few days.

Sam

---

### Post by notlistening on 2008-11-16
Hi Sam,


The initial work that i have done was proof of concept and it works under SAPI 5.1 but with quite a large amount of complex sticky tape work. The current version of Wine does not play niceley with the SAPI installer.

Microsoft have been a little bit sneaky. They have included the SAPI 5.3 SDK files within the Vista SDK package. To work with the Vista SDK you will need to identify and extract the required files and make your own install package for Wine. Similar to the process that i will be using. I see the work that you are doing as the next natural step and would welcome you to make a start.

I am using some less popular technologies and would not expect you to use them but they do provide the basis for a working model and test environment.

I have not looked at the legality of using either SAPI 5.1 or 5.3 might cause when used in this way. 

Oh well if it is popular then it will catch on.

Hope to catch up soon.

Tom

---

### Post by Ohmu on 2008-11-16
Check this link!

[http://www.geekpedia.com/Thread16235_Windows-Server-2008-And-Speech-Recognition.html]("http://www.geekpedia.com/Thread16235_Windows-Server-2008-And-Speech-Recognition.html")

This guy has ported SR from Vista to WinServer08.  He details the files and registry settings that need to be copied over.  

I'll copy the relevant part of the page here, to keep things together.

[INDENT]Okay. So I DID get it to work but I can't tell you the exact steps but I can
tell you what I did and what I think matters. Hopefully someone else can
narrow this list down to what counts. Or even better, someone from MS support
can actually reply to one of the 5 messages posted. What you need: Machine A
with server 2008 and Machine B with MS Vista (FYI - my vista is NOT on SP1
yet so that shouldn't make a difference)
NOTE - ALL copies were done w/out writing over current files, I left
existing items in place.

1. Copy from vista(a must) C:\windows\system32\speech
2. Copy from vista(a must) C:\windows\speech
3. Copy from vista (prob not needed) C:\windows\assembly
4. Copy from vista (prob not needed)
C:\Windows\Microsoft.NET\Framework\v2.0.50727

Registry Changes (do at own risk but this is the most crucial part) Now, I
am not sure how classids are created but i THINK (please correct if wrong)
they are unique to each machine which i think caused issues for me but if I
am wrong, and I hope I am, someone can actually provide a list of which ones
matter.
1. Export from vista(a must) HKLM\Software\Microsoft\Speech
2. Export from Vista (optional?) HKCU\Software\Miscrofot\Speech

Now the hard part. There are references of GUIDS that matter (its the
objects that look like this: {DAC9F469-0C67-4643-9258-87EC128C5941}
Find everyone one of those under the registry objects you just exported in
Vista and export to server 2008. Really, the ones I think matter are the HKLM
and HKCR. If you did the current user then you should continue and do the
HKCU as well. This is the most tedious part, but i think its a must.

Do not overloook this-> HKLM\Software\Classes\CLSID just because you did HKCR

And lastly, (this is what I think finally got it workin). On vista look for
every registry reference to the following files and bring those objects over
(mainly its the classids again inside of HKCR and
HKLM\Software\Classes\CLSID).

C:\Windows\System32\Speech\Engines\SR\spsreng.dll
C:\Windows\System32\Speech\Engines\SR\spsrx.dll
C:\Windows\System32\Speech\Engines\SR\srloc.dll

Other actions I took or variables that I don't think matter, but I wanted to
share. My vista OS is ultimate (but ANY vista should work). I had installed
speech recog server 2007 (which you can download from MS) on server 08 and
vista. I installed windows SDK for server 2008 on both machines and compiled
and registered the sample recognition engine (which doesn't do anything).

I think that covers it. It was a horible process that most likely people
will not want to attempt, but i promise you it is possible. I think its all
about know which reg keys to export and the basic files. I hope MS releases
something to make it easier because it should be a very simple update for
them. If my server crashes i would be very bummed. (now to take an image of
my server)[/INDENT]

---

### Post by drbongo on 2008-11-18
Greetings 'notlistening' drbongo here!

I was going to recommend that the people interested in getting sapi working on ubuntu with wine get in touch with you, but it seems that you are already contributing to the thread. I have just signed up for the accessibilty team and found your tasteful 'brokeback mountain' style picture which I presume was taken during the breast cancer awareness week!

I am currently working on remastering Ubuntu with the accessibility options enabled. Initially three versions one with speech, one with magnification and one with both. Then I will need to test as many applications as possible to see what can be done and what can't.

Keep in touch!

drbongo

---

### Post by notlistening on 2008-11-19
Hi Dr.

I started the post a bit ago and have got very little interest. Lots of people want it but there are not to many people who are interested in working on it. I am setting up my website [http://www.vipsight.info](http://www.vipsight.info) to host some information, guides and downloads. If you have a spare 65 MB and use speech dispatcher then I can do you a SAPI install. Soon I will write a few useful tool as examples but for now time is short. 

Tom

---

### Post by drbongo on 2008-11-19
Hi Tom,
Keep me in the loop, as you know my 'Linux Development' time is somewhat limited during working hours as my employers want software they can sell, but I am happy to try out anything you develop or assist you if I can in my own time!

I am planning to focus on making accessible remixes of Ubuntu in the short term, In the longer term I am hoping to make some accessible apps using the Gambas IDE which will be installable on any of the major Linux distros such as Debian, Ubuntu, Fedora and Suse etc.

I will post any developments or queries to this forum which might be the best way to keep in touch.I will start a new thread when I have anything worth posting!

drbongo

---

### Post by Ohmu on 2008-11-23
From talking with NotListening, I learned this:

He has put the project up here:
   [http://code.google.com/p/open-sapi/](http://code.google.com/p/open-sapi/)

he got SAPI5.1 Redist* working on AND OLD VERSION of Wine.  ie 'wine SpeechSDK51.exe' ( google "SpeechSDK51.exe" to download it from M$ )

This was the version that came with his Gutsy Gibbon Ubuntu.   But he doesn't know the exact version number.

It WON'T WORK on a new version of Wine (eg 1.1.8).  The installation says it's completed, but it hasn't.

So he's done something like:
   mv .wine .wine_backup
   UNINSTALL Wine old version
   INSTALL new Wine
   rm -rf .wine
   mv .wine_backup .wine

And this WORKS.  He can train the Voice, and dicate into SimpleDictation.exe.

I have tried replicating this, 
a) by using his .wine directory (FAILS)
b) by  
- uninstalling wine, 
- downloading & installing Wine 1.0 from here:
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)
- installing: 'wine SpeechSDK51.exe'
(FAILS - log below)

Can someone try to get this working?

Sam



PS Log for b) reads (killing duplicate lines):

fixme:advapi:LookupAccountNameW (null) L"sapi51b" (nil) 0x33f77c (nil) 0x33f780 0x33f774 - stub
fixme:advapi:LookupAccountNameW (null) L"sapi51b" 0x134c60 0x33f77c 0x134e30 0x33f780 0x33f774 - stub
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub SelfUnregModules -> 1 ignored L"SelfReg" table values
fixme:msi:msi_unimplemented_action_stub UnregisterTypeLibraries -> 9 ignored L"TypeLib" table values
fixme:msi:msi_unimplemented_action_stub UnregisterProgIdInfo -> 131 ignored L"ProgId" table values
fixme:msi:msi_unimplemented_action_stub RemoveShortcuts -> 26 ignored L"Shortcut" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 7 ignored L"CreateFolder" table values
fixme:msi:ITERATE_CreateShortcuts poorly handled shortcut format, advertised shortcut
fixme:msi:ITERATE_CreateShortcuts poorly handled shortcut format, 
fixme:shell:DllCanUnloadNow stub
err:msi:register_progid L"Srdrv1.Alternates.1" has no class
err:msi:register_progid L"Srdrv1.JapanesePhoneConverter.1" has no class
err:msi:register_progid L"Srdrv1.ChinesePhoneConverter.1" has no class
err:msi:register_progid L"Srdrv1.Alternates" has no class
err:msi:register_progid L"Srdrv1.JapanesePhoneConverter" has no class
err:msi:register_progid L"Srdrv1.ChinesePhoneConverter" has no class
Successfully registered DLL C:\Program Files\Microsoft Speech SDK 5.1\Bin\SREng.dll
err:menubuilder:InvokeShellLinker failed to build the menu
fixme:shell:DllCanUnloadNow stub

---

### Post by notlistening on 2008-12-11
Look a the forum hijacker above :P. Thanks Tony for the hard work and it would be great to intergrate a version with a SAPI engine installed at some point, that might be sold for a small amoutn of money as good SAPI engines are not free yet.

Great news, I can now reliably install SAPI in wine. After about ten hours of regression testing i have identified the bug that is causing the problem and submitted this to the wine team. 

To install the Microsoft Speech SDK you must set the global application defaut environment to Windows 2000 in the winecfg utility. This seems to make the installer behave as it should. 

*Edit* The latest build direct from wine does not support audio in Ubuntu, please install the Ubuntu specific package. 

Next i am writing the command line interface and setting out the functionality of the server. Getting there slowly.

Tom

---

### Post by drbongo on 2008-12-12
Forum Hijacker here! I am pleased to hear you have managed to solve the SAPI/Wine compatibility problems. I presume once you have sapi running in wine you can then install and or run windows sapi applications with wine as well. Question: will the sapi engine be available to linux apps or Orca etc or will its use be restricted to windows apps running in wine? Obviously if it works with native linux applications that will open a whole host of new possibilities, but even if it is restricted to wine it will be great! Nightmare scenario - T3 works on Linux!- (PRIVATE JOKE).

PS Sarah showed me the card you sent her today, she carries it everwhere with her, aah! Your just so romantic!

---

### Post by notlistening on 2008-12-12
The idea is to have the speech engines both test to speech and speech to text available to the native linux apps. As a starting point i am using Speech Dispatcher to try integrating into the Gnone destop this will allow any compatible software Orca Emacs etc to work with it and again provide proof of concept in regard to performance. Also it is possible to add speech into any existing app with a socket and a little bit of text processing. 

Wait for the sea of TCL apps that i will have soon. Any ideas for something that is currently missing from you life then drop me a line about a test app i can write for you.

Tom

Wishing TCL was more widely adopted.

---

### Post by notlistening on 2008-12-16
Moving forward still. :) I have managed to get a much smaller download for the TTS speech side of the MS Speech SDK just 6.5 MB which gives all the free voices. I have managed to get the MSI to install unattended in wine but the win 2k issue still resides even in these new installers.

I will again see if i can rally some support on the wine forums.

If anyone has some basic speech dispatcher development skills they might lend me i still need to modify the baisc speech dispatcher command line driver as the first stage before moving to the server client version.

---

### Post by notlistening on 2009-01-16
The SAPI server and client are now running.

I have the Microsoft speech engines installed and running along with a Voice Ware engine called kate. These are working without too many problems. For testing purposes I am using aMSN running natively in Ubuntu with the voiceIT plugin modified to use the OpenSAPI client to send new messages to be spoken. The only problems encountered so far is with PulseAudio crashing every so often.

So next is to get speech dispatcher running with it and to test it fully using Orca.

Then to package it up nicely and hand it out. A link to the wiki with instructions on how to install and configure the system will follow shortly.

I love it when a plan comes together.

Tom

---

### Post by notlistening on 2009-01-18
A Saturday of work has speech dispatcher working with orca and it runs very nicely, one of those pleasant surprises.

Still some bugs to be ironed out with debugging as there are issues with Speech Dispatcher killing the client before it has sent the debug information back but this was only a development mechanism and I will start using log files.

Next a simple installer and the rest of the functionality that is still missing :)

:guitar:

Tom

---

### Post by PmDematagoda on 2009-01-18
drbongo, please keep the posts related to your issues or topics within their respective threads instead of hijacking another user's thread.

Please consider this to be your first warning, a second occurrence may not be tolerated so leniently.

---

### Post by notlistening on 2009-02-23
Well the development continues at snails pace but hey that my speed. I have now moved on from freewrap even though i love the application and its ease of use it is not supporting threads and due to the threaded nature of the SAPI TTS engine, i needed a way to monitor and run code that blocks at the same time as remaining responsive for communiction from clients.

I am now packaging with starkits and tclkit which combined make starpacks; a stand alone executable. To support threading i am having to use the latest version of wine from their repositories and that seems to work fine but this further complicates the steps needed to install. Fingers crossed the Ubuntu teams add a version that works in their next release.

Tom

---

### Post by notlistening on 2009-03-25
Calling all developers. This site now has code downloads and basic wiki information. It will enable you to see it working, well kinda, there are bugs, no error handling and only the very basic information on the wiki. Please come on the discussion board ask question give feedback, hack the code. You want to help there are too many todo jobs to list but that can be found on the wiki. If you ask for more details I will explain what needs doing in greater detail. 

See Google Code:
 
[http://code.google.com/p/open-sapi/](http://code.google.com/p/open-sapi/)

There is an open discussion group here:

[http://groups.google.com/group/open-sapi](http://groups.google.com/group/open-sapi)

alternatively mail me directly with problems there will be 100's. 

:lolflag:

Tom

---

### Post by AICollector on 2009-03-27
I would very much like to get my 16kh SAPI voice working in Ubuntu! :D

Just an idea; some tools on Windows let you use the SAPI system to read out a txt file and turn it into a .wav or .mp3 (for later listening) I used to do this to turn a few good books from Project Guternburg into audiobooks.

Any chance I might see similar functionality with this, I wonder?


It's probably also worth noting most programs like this could also allow the user to make the computer pronounce words diffrently.


When your a bit further down the line (IE: you've got an interface an idiot like me can use) I will be more then happy to help!

---

### Post by notlistening on 2009-03-27
Yeah the basics have already been done and the system will produce wav files on demand, the code is just not released yet. The prenounciation is an issue i have looked at a little but feel that it is doable as well.

Tom

---

### Post by plantatree on 2009-05-01
> **AICollector said:**
> I would very much like to get my 16kh SAPI voice working in Ubuntu! :D

Just an idea; some tools on Windows let you use the SAPI system to read out a txt file and turn it into a .wav or .mp3 (for later listening) I used to do this to turn a few good books from Project Guternburg into audiobooks.

Any chance I might see similar functionality with this, I wonder?


It's probably also worth noting most programs like this could also allow the user to make the computer pronounce words diffrently.


When your a bit further down the line (IE: you've got an interface an idiot like me can use) I will be more then happy to help!

In fact there is a free editor Saypad that can read to wave and mp3 as well can split up files given a chapter break. I use it through wine to prepare books for my wife. It's a little bit of a hassle to get used to it though. As well for every file I have to restart the editor.

As well it has another drawback. Only the standard 3 sapi voices are selectable through it. But I wanted to use a separate voice because of my language. So eventually hacked the voices' names in the windows/wine registry and now MS Marry is the voice I want to read with :)

Experimenting with open-sapi now. Unfortunately I'm facing an issue with speech-dispatcher not processing cyrillic. [http://lists.freebsoft.org/pipermail/speechd/2009q2/001695.html](http://lists.freebsoft.org/pipermail/speechd/2009q2/001695.html)

---

### Post by notlistening on 2009-05-30
Latest developments, now open SAPI seems to work in other languages. It is hard coded at the moment so there is no flexibility on the encoding used but the proof of concept is there again and keeping a few users happy.

Tom

---

### Post by notlistening on 2009-06-05
Right this now requires testing from people. The default wine version in Ubuntu even 9.04 is not stable enough when it comes to running threads so you need to get the latest version of wine for a reliable system. Currently in the testing phase and require people who can use a terminal to get stuck in.

NL

---

### Post by notlistening on 2009-08-25
I now have a very stable version of the software running without crashes. I do not use this as my main way to access the computer as i have enough sight to use a magnifier.

It would be great again if you guys could test the system. It is important to update to the latest binary version of wine from the wineHQ website. This improves stability. Otherwise i am using the current version of speech-dispatcher and Orca in 9.04 with small modifications to the speech dispatcher setup. This can all be downloaded from the project website and there is a wiki giving installation and usage instructions.

This software is still in the development stage but coming along slowly. Please try it out and see. 

Tom

---

### Post by notlistening on 2009-11-02
What's new:
Vista TTS engine installed and working
Threaded model working smoothly
Gnome Lockups fixed
Delays and freezes fixed 


The release of Karmic Koala has created an opportunity for open-sapi. The latest release of Ubuntu has seen a few usability problems introduced for text to speech users. Reliability, latency issues with the audio subsystem and generally the move toward pulseaudio that ubuntu seem to be pushing for seem to be making the system unstable and unusable.

A mist these changes it has been just in time for open-sapi. With the latest development version as yet unreleased ( The setup is a real pain by the way at the time of writing this) open-sapi in its second generation is out performing espeak on karmic. 

The clarity of speech is much clearer even with the basic Microsoft (free engines) it is significantly more responsive. Delays and blocking behaviours previously seen are now a thing of the past.

This has been achieved using a threaded approach but has come at the cost of having to use a more up to date version of wine. As wineHQ have not released a wine version for Karmic it meant building from source or using the Jaunty repository (untested).

This is further complicating the open-sapi install. The plan is to create my own PPA with the a stable wine version for use with open-spai until Ubuntu decide to update to a later wine version.

I have to iron out a few bugs with how the system loads and runs, package the open-sapi files into a .deb file for the first release, find a way to install SAPI and submit the first round of changes to speech-dispatcher.

Tom

---

### Post by notlistening on 2010-03-23
Latest News,

So where we are now. I have a reasonably stable open-sapi that runs with Speech Dispatcher and Orce through wine. It is fast responsive and sounds nice. Changing the voice in open-sapi is a pain at the moment and none of the Orca setting pitch, volume and rate actually take affect . If people would like a sneaky peak I can get the pitch volume and rate all working and release a pre-Alpha deb. Let me know if your interested. 

Change Log:
[LIST]
[*]Fixed command line bugs with ?
[*]Enable file/wav format changes
[*]Enabled wav file output
[*]Streamlined Code
[*]Moved to a multi threaded model
[*]Reworked the debugger to use threads
[*]Reworked speech output to use threads
[*]Rework audio output to use Memory Streams
[/LIST]


A recent move to Lucid has meant that open-sapi had to evolve in a new direction. 

The update of wine in Lucid was a very much needed component for open-sapi to even run under Ubuntu. This now allows for the multi threaded server to run smoothly with significant performance improvements with open-sapi responsiveness and application start up times. 

However with every update comes another problem. We are supposed to call it progress.

The wine ESD sound driver is soo out of date that pulse audio and wine are no longer best friends and the audio is sometimes distorted sometimes not, with lots of pops and fizzes on the output. Also from what I read this is different depending on your hardware. So using the wine audio subsystem is not really viable anymore for open-sapi. 

So I have begun development to get RAW audio data from sapi and pass that to the client who can do what they want with it. The proof of concept is done and I have RAW audio streams that I can process, redirect anyway I want. This was a big project milestone as it was a stopper on the development of the Speech Dispatcher module. Also it allows me to follow on to actually creating a speech server which can output multiple streams to multiple clients at the same time.

NL

---

