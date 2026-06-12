---
title: "High quality text to speech GUI"
date: 2013-09-11
forum: Assistive Technology &amp; Accessibility
---

### Post by frytek on 2013-09-11
You can play with a multi-language* text reader which uses SAPI to produce high quality speech. The name is *sbreader*. The program reads the file aloud with good quality voices while highlighting sentence-by-sentence. Machine translation of the text is available (MS translation engine API key is required). The plan is to generate audio files from the text.


    *Currently it reads latin- and cyrillic-based languages. If you want to read, say, Katakana or Hiragana, you're welcome to participate in the project.


    The download link: [http://tts.polip.com/files/sapi/](http://tts.polip.com/files/sapi/) - please choose the newest version of* sbreader* available.

    Requirements:
    python-pyspda, python-sapilektor, python-requests, python-gi, gir1.2-gtk-3.0, gir1.2-gtksource-3.0

    and a running SAPI server. To install SAPI on your Linux box you need, as I wrote in some of my previous posts:

    [I]ppa:
    sudo add-apt-repository ppa:ethanak/milena
    
    [EDIT: we also need wine version >= 1.7 - please specify it while installing (or click the right version in package manager) - otherwise you might get an older, stable version. ]

    sudo add-apt-repository ppa:ubuntu-wine/ppa

    sudo apt-get update
    [/I]


    and packages:
   * sapi4linux, libsapilektor, libsapilektor-utils, wine.* Then check the README file in /usr/lib/sapi4linux/ on how to install and run.

    Basically, to use Infovox voices, just copy (or symlink) the voice demo .exe (something like infovox3_100demo_Hans22k.exe) file to */usr/lib/sapi4linux/infovox_demo*. 
    [ Edit: I know these voices have disappeared from the known universe. I do not have them, please don't ask me. ]

Ivona demo voices can be downloaded with use of the *ivona_download* script. Use -l to list available voices and the voice_name to download the one you chose. (The script can take a considerable time to run! In case of failure, try to run it again.) Or download the demo as described in a README file directly from the site (it will require some exchange of emails, though.) Then, save or symlink the .dat files to * /usr/lib/sapi4linux/ivona_voices*. 


    The voices (.exe or .dat) files should be copied or symlinked to their directories prior to running the *install_sapi_server -f* command. After this, run *sapiconfig -n -s *to save the discovered voices in the config file.

    Try the voices with *sapitest* - if they work you are ready to try *sbreader*. Please notice, that the txt file must be encoded in utf8.


   To guess language of the file automatically:
sudo apt-get install python-setuptools
sudo easy_install guess-language

---

### Post by ethanak on 2013-09-13
To enable file encoding autodetection (since 0.1.3):
sudo apt-get install python-chardet

---

### Post by frytek on 2013-12-05
December 2013: 
It seems there are problems with some (all?) new versions of Ivona voices. Adding such a voice to the ivona_voices directory will cause the SAPI server to stop. This means that all the voices (previously working demos or even full, registered versions) will not be available. 

The problem is being handled. If in doubt, just use Infovox for a while. Send me a private message if you have any problems.

---

### Post by jacquin.t on 2013-12-13
Hi,

I follow your instructions and successfuly installed my 2 french voices. Now I would like to build an mp3 from a .txt.

I'm using this command :

sapilektor -a -r -s 1.3 -v celine test.txt - | lame --preset voice -r -m m -s 22050 - test_celine_ivona.mp3

but I have this error :

```

Error: 500:Internal error: Traceback (most recent call last):
  File "ssapi.py", line 280, in speak
    self.server.speaker.speak(data)
  File "<COMObject SAPI.SpVoice>", line 2, in speak
com_error: (-2147352567, 'DISP_E_EXCEPTION', (0, None, None, None, 0, -2147221164), None)

```

This command works using a default voice.

I would like to try using Infovox voices but I don't find where to download french voices.

Thank you in advance.

EDIT : I found french Infovox voices here : [http://dl.accessolutions.fr/demos/Infovox/](http://dl.accessolutions.fr/demos/Infovox/)

When I restart the installation of sapi server voices seems to be installed because I have : Voice Installed at each step.

But at the end when I check the config (*sapiconfig -n) *none of my Infovox voices are in the file.

Here the installation detail :

```

Changing current directory to /usr/lib/sapi4linux
No Ivona voices found
infovox_demo/infovox3demo_Alice22k.exe
infovox_demo/infovox3demo_Bruno22k.exe
infovox_demo/infovox3demo_Julie22k.exe
infovox_demo/infovox3demo_Antoine22k.exe
infovox_demo/infovox3demo_Claire22k.exe
infovox_demo/infovox3demo_Louise22k.exe
infovox_demo/infovox3demo_Margaux22k.exe Infovox3 demo voices found
Screen already exists
299:Shutdown OK:
Shutting down wine
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: created the configuration directory '/home/adraesh/.winesapi'
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: configuration in '/home/adraesh/.winesapi' has been updated.
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
Setting Windows version to win2k
Clearing Windows version back to default
Installing infovox_demo/infovox3demo_Alice22k.exe
Accepting instalation
Accepting license
Setting installation path
Setting menu path
Setting apps
Unselecting icon and firewall
Installing
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
Killing application and installer
5460  Started...
Voice installed
Installing infovox_demo/infovox3demo_Bruno22k.exe
Accepting instalation
Accepting license
Setting installation path
Setting menu path
Setting apps
Unselecting icon and firewall
Installing
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
5460 Already Started... press a key
Killing application and installer
Voice installed
Installing infovox_demo/infovox3demo_Julie22k.exe
Accepting instalation
Accepting license
Setting installation path
Setting menu path
Setting apps
Unselecting icon and firewall
Installing
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
5460 Already Started... press a key
Killing application and installer
Voice installed
Installing infovox_demo/infovox3demo_Antoine22k.exe
Accepting instalation
Accepting license
Setting installation path
Setting menu path
Setting apps
Unselecting icon and firewall
Installing
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
5460 Already Started... press a key
Killing application and installer
Voice installed
Installing infovox_demo/infovox3demo_Claire22k.exe
Accepting instalation
Accepting license
Setting installation path
Setting menu path
Setting apps
Unselecting icon and firewall
Installing
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
5460 Already Started... press a key
Killing application and installer
Voice installed
Installing infovox_demo/infovox3demo_Louise22k.exe
Accepting instalation
Accepting license
Setting installation path
Setting menu path
Setting apps
Unselecting icon and firewall
Installing
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
5460 Already Started... press a key
Killing application and installer
Voice installed
Installing infovox_demo/infovox3demo_Margaux22k.exe
Accepting instalation
Accepting license
Setting installation path
Setting menu path
Setting apps
Unselecting icon and firewall
Installing
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
5460 Already Started... press a key
Killing application and installer
Voice installed
rebooting wine
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000
5460  Started...
Creating server wrapper command in /home/adraesh/bin/sapi_server.sh
Creating Ivona voice download command in /home/adraesh/bin/ivona_download.sh
Running server

```

Thank you.

---

### Post by frytek on 2013-12-19
Update: I got some information that new versions of voices seem not to work with sapi4wine. 

If your SAPI server crashes during installation after symlinking some voices to installation folders, use only either version 3 Infovox demo voices or versions of Ivona voices downloaded before mid 2013. 

I don't have these files available so please don't ask me for them. 

Working old Infovox voices version 3 are available here for many languages: [http://www.acapela-group.com/infovox3-37-3-speech-solutions-tts.html](http://www.acapela-group.com/infovox3-37-3-speech-solutions-tts.html)
[Edit: Infovox 3 seems to be gone. The page now redirects to version 4 with limited numbers of voices available - I didn't check them yet.]


Ivona voices: I have no information. Voices downloaded from the official website after mid 2013 will probably not work with sapi4wine (you have to check it yourself for specific languages) but you might be able to find some cashed files on the internet. sapi4linux is not supported by Ivona or Amazon so asking questions to their technical support is futile.

---

### Post by alexei.colin2 on 2013-12-26
How would one diagnose why an IVONA voice is not detected at all: install_sapi_server explicitly tells me 'No IVONA voices detected'? Any logs or debugging output or a pointer into the source code? My issue doesn't seem to be related to the above issue with new voices causing trouble because these files are from 2012.

If I use a new IVONA Salli voice (downloaded now as instructed in the README), then I get the following (while the default preinstalled voices do work fine):
```

$ sapitest -v Salli hello world
Error: 500:Internal error: Traceback (most recent call last):
  File "ssapi.py", line 280, in speak
    self.server.speaker.speak(data)
  File "<COMObject SAPI.SpVoice>", line 2, in speak
com_error: (-2147352567, 'DISP_E_EXCEPTION', (0, None, None, None, 0, -2147221164), None)
```
EDIT: Sorry, didn't read the above carefully enough, it's the same error reported above, but my question still holds:
Is this exactly how the new voices fail, or am I having some other problem?


Btw, I'm guessing you are not affiliated with [this OpenSAPI project]("https://code.google.com/p/open-sapi/")?

---

### Post by alexei.colin2 on 2013-12-26
> **jacquin.t said:**
> 
EDIT : I found french Infovox voices here : [http://dl.accessolutions.fr/demos/Infovox/](http://dl.accessolutions.fr/demos/Infovox/)

When I restart the installation of sapi server voices seems to be installed because I have : Voice Installed at each step.

But at the end when I check the config (*sapiconfig -n) *none of my Infovox voices are in the file.

Here the installation detail :

```

preloader: Warning: failed to reserve range 00007ffffe000000-00007fffffff0000

```


Just for test purposes (don't speak French), I have installed the infovox3demo_Alice22k.exe from your link and it was detected correctly by 'sapiconfig -n': 'sapitest -v Alice hello world' worked. Strange it's not working for you. The only real difference between the logs seems to be the quoted warnings (I don't have them). But this also suggests the other potentially significant difference: I'm on a 32bit machine.

Also, here's my wine package version: 1.4-0ubuntu4.1. EDIT: And, I can confirm that for wine 1.6 the voice installs but is not detected (as you describe).

>  Working old Infovox voices version 3 are available here for many languages: [http://www.acapela-group.com/infovox...tions-tts.html]("http://www.acapela-group.com/infovox3-37-3-speech-solutions-tts.html")

The links are there but they are broken (redirects to some easy-access page). I can successfully download the v4 files from a similar page and similar links, but not these ones. I've checked some files from some other sources but they are must not be the correct v3 demo ones since they result in 'Installer error'. If anybody tracks the v3 demo files (like the French ones above) please post.

EDIT: another question:
Do the Infovox demo installers come bundled with SAPI? As far as I see, they do not. So, sapi.msi from open-sapi is installed (otherwise the COM interfaces are not created at all). Then, what is the version of the SAPI in this sapi.msi -- open-sapi website doesn't specify what exactly is packaged in this msi? Finally, Infovox v4 installer fails at RegSvr32'ing the acattsapi5.dll, which maybe suggests that v4 depends on a newer SAPI installation. To complicate things, Microsoft doesn't distribute SAPI installers, but only Merge Archives (.msm) for application developers to bundle with their apps. So, do you think Infovox depends on a standalone SAPI install, and if so, where do we get it?
EDIT: From Ivona installer, I can see that Ivona installer does indeed come bundled with exactly the several MSM files for SAPI5 instructed by Microsoft (and they come already converted to msi).

EDIT: no luck in installing Infovox v4: tried wine1.4 wine1.6 wine1.7*, tried installing into clean wineprefix Microsoft-English-TTS-51.msi instead of the bundled sapi.msi -- same regsvr error.
* NOTE: wine1.7 pops up a 'mono not installed' dialog, which would remain and hang there hidden if you use the hidden display, so do what install_sapi_server does manually on the main real display.

UPDATE: Ivona: when installed manually (in Windows 2000 wine mode -- otherwise, the sapi.dll is not registered as the COM server), the new evaluation version installs and is detected by sapiconfig, but it fails when accessed by the client due to unimplemented stub MSVCP110.dll.?setw@std@@YA?AU?$_Smanip@_J@1@_J@Z. [Bug report filed to wine]("http://bugs.winehq.org/show_bug.cgi?id=35237"), but there little hope. This is both on wine 1.6 and 1.7.8
Older versions of Ivona that I had install but the trial is reported to be expired (and what works on Windows doesn't work).

---

### Post by alexei.colin on 2013-12-26
At last: NeoSpeech Voice (Bridget) installed smoothly and works smoothly.

The sound needed some [equalizer]("http://askubuntu.com/q/72679/88055") fiddling to cut the high-frequency ringing noise, but otherwise all good. The sbreader is working nicely!

Some notes to those on the same path:
 [S](1) sbreader supports the [unofficial TTS API from Google]("http://askubuntu.com/q/72679/88055"), which is fairly good quality, so you don't even need to fiddle with the voices if that's good enough[/S] EDIT: Sorry, was wildly confused. Sbreader has something about translation via Google, not TTS..

 (2) SAPI voices packages are essentially DLLs that implement the COM interface defined by SAPI (sapi.dll). The voice DLL is the only point of entry; the installer and how the engine data is stored and accessed are completely custom to each voice (for example, Ivona's installers are executables with '.dat' extension, go figure). Installing a voice, in essence, is registering its DLL as a COM server using regsvr32 -- each installer is responsible for doing this.

 (2) SAPI4Linux goes to great length to automate voice installation (e.g. to allow you to do no more than drop the installer file into the folder), which is nice, but keep in mind that it is not doing anything special in terms of installing the voice: you can simply install any SAPI5 voice using 'WINEPREFIX=~/.winsapi wine ~/my/voice/setup.exe'. Also, most voice installers package SAPI DLLs, so it doesn't strictly need to be installed separately.  When voice fails to install or to work, it most like has nothing to do with open-sapi or sapi4linux. The installation is completely the responsibility of Wine -- it amounts to running the Windows installer.

 (4) To make the DLL registrations succeed, set Windows 2000 mode in 'WINEPREFIX=~/.winesapi winecfg'

 (3) For diagnosis of the server during runtime, change the 'display' variable in install_server.sh to ':0' so that you get to see any dialogs (like 'Trial expired') if they come up. Also, you can start the server in foreground to track its output: 'WINEPREFIX=~/.winesapi wine pydir/python.exe ssapi.py -a all'

---

### Post by charlie.picorini on 2014-01-09
Hi,

First of all thank you very much for this amazing thread:), namely for the French voices which were still available 2 weeks ago via the provided Infovox link. Unfortunately It looks like the voices have moved out ...

I followed too the detailled steps provided by frytek and it worked. The quality increase between Google TTS and Acapella voices is huge (you can listen to the result from [http://x.platformeasytools.free.fr/download/balados/SecurityNow/SN_434.mp3](http://x.platformeasytools.free.fr/download/balados/SecurityNow/SN_434.mp3)). My [project]("http://x.platformeasytools.free.fr/wiki/index.php?title=Main_Page") (translate the great Security Now! Podcast into French via voice synthesis) is benefiting a lot from your method:p.

I wrote a little tutorial in French (following exactly your instructions) that may help French people to install all needed tools: it is available on [http://x.platformeasytools.free.fr/wiki/index.php?title=M%C3%A9thodeSAPI](http://x.platformeasytools.free.fr/wiki/index.php?title=M%C3%A9thodeSAPI).

I spent some time trying to install everything on my 64 bit Linux version, until I realised that** a 32 bit environment was needed** (as [**[COLOR=#000000]alexei.colin2[/COLOR]**]("http://ubuntuforums.org/member.php?u=1893315") reported) for everything to work, I guess because of Wine. So I installed everything from a 32 bit Ubuntu running in a virtual machine. Does anybody experience the same need for 32 bit environment ?

@alexeicolin2: they say on WineHQ that the missing function has been implemented recently. I will try your advices with Ivona voices when the new version of Wine is out. Correct me if the method is not exactly the one you are suggesting:

1) Install Sapi4Linux as described by frytek

2) Install the latest version of Wine that implements the missing function

3) Set Windows version to Windows 2000 in Wine Configuration (was already set to that for me)

4) Download Ivona voices and then simply run 'WINEPREFIX=~/.winsapi wine ~/my/**Ivona**Voice/setup.exe' for each voice ?

5) Run [I]sapiconfig -n -s and sapitest with the new voices

CYA[/I]

---

### Post by frytek on 2014-01-17
"At last: NeoSpeech Voice (Bridget) installed smoothly and works smoothly."

Could you add some details? I could not find any place to download it...

---

### Post by jacquin.t on 2014-01-25
Hello everyone,

I would like to know if some of you have a previous version of ivona english voice who works with sapi4linux ?

Thank you in advance.

---

### Post by Hydranix on 2014-02-09
I could be misunderstanding your posts (both this one and the one which links here: [2111436]("http://ubuntuforums.org/showthread.php?t=2111436")) but from what I've read is that you are looking for a GUI text-to-speech program.

While searching you were able to get high-quality commandline based TTS to function properly.



Why not just use a script to wrap that commandline TTS with a gui?

I would use YAD for this purpose. [http://sourceforge.net/projects/yad-dialog/](http://sourceforge.net/projects/yad-dialog/)

```

#!/bin/sh
# --------------------------------
#  Dirty TTS GUI by Hydranix
# --------------------------------
speak() {
    echo \'${@}\'|festival --tts &>/dev/null
}


QUIT=0


while [ "$QUIT" -eq "0" ]; do
    TEXT="$(yad --width 200 --height 100 --title="Hydranix TTS Wrapper" --center --skip-taskbar \
        --form --dialog-sep --entry \
        --entry-text="Speak this text..." --editable \
        --button="Speak":20 \
        --button="Cancel":1)"
    case $? in
        1) speak "Canceled"; QUIT=1; exit 0;;
        20) speak ${TEXT};;
        255) speak "Canceled"; exit 0;;
        *) speak "Canceled"; exit 0;;
    esac
done

```

---

### Post by alexei.colin on 2014-05-03
(Sorry, didn't get notifications for this thread for some reason.)

> **frytek said:**
> "At last: NeoSpeech Voice (Bridget) installed smoothly and works smoothly."

Could you add some details? I could not find any place to download it...

NeoSpeech voices are for sale, but it appears to be quite hard to find a distributor for it (have to [contact company directly]("http://www.neospeech.com/tts-engine.aspx")). The version that worked for me is a 2010 release of Bridget (UK). I just ran the installer via Wine as described above. The voice was then recognized by sapi4linux, and was selectable in sbreader. I'm still using it successfully, so ask for details as needed.

[QUOTE=charlie.picorini]
@alexeicolin2: they say on WineHQ that the missing function has been implemented recently. I will try your advices with Ivona voices when the new version of Wine is out. Correct me if the method is not exactly the one you are suggesting:

1) Install Sapi4Linux as described by frytek
2) Install the latest version of Wine that implements the missing function
3) Set Windows version to Windows 2000 in Wine Configuration (was already set to that for me)
4) Download Ivona voices and then simply run 'WINEPREFIX=~/.winsapi wine ~/my/IvonaVoice/setup.exe' for each voice ?
5) Run sapiconfig -n -s and sapitest with the new voices
[/QUOTE]

Yes. Just to be clear, in Step 4, the argument to wine would be the path to the voice installer, the path and the name might be different from the example above. Please report back once you try the Ivona voices in a wine version that has that function implemented.

---

### Post by frytek on 2014-06-02
Summarizing: to be able to use new Ivona voices, we need wine version >= 1.7.18

To install it we need to add the repo: 



sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine




:)

---

### Post by dom8 on 2014-08-10
Hello all, many years have been waiting for TTS on linux 
today installed on linux mint 17: 
wine beta
Ivona voices
Ivona reader 
and it's working!!! well almost 
reading rrs,written text
but can't copy text to clipboard monitor or even option paste text not working 
any ideas?
**option**

---

### Post by dom8 on 2014-08-11
solved with clipboard manager ,ctrl+v still not working but middle button on mouse do the job ;-)
**clipboard**

---

### Post by jacquin.t on 2014-08-13
Hi everyone,

Well since severals months everything works perfectly, I am able to generate mp3 using wine server sapilektor and everything I had installed following the first post of this thread.

Since today, nothing works. In fact I updated my ubuntu server to 14.04.1 LTS and I have done what I done everytime I restart my server : relaunch install_sapi_server -f

But it doesn't work, at the end of the installtion I try to launch sapiconfig -n or -s and the script doesn't end. When I launch sapilektor I have the error message : **No SAPI voices declared**

Here the output of the install_sapi_server -f (Everything looks great) :

> 
Changing current directory to /usr/lib/sapi4linux
2 Ivona voices found
No Infovox3 demo voices found
Screen already exists
299:Shutdown OK:
Shutting down wine
wine: created the configuration directory '/home/adraesh/.winesapi'
wine: configuration in '/home/adraesh/.winesapi' has been updated.
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
Setting Windows version to win2k
Clearing Windows version back to default
Disable sound
Installing ivona_voices/celine.dat
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
Installing ivona_voices/salli.dat
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
Ivona voices installed, reinstalling sapi
Setting Windows version to win2k
/usr/bin/install_sapi_server: line 101: 20934 Terminated              /bin/bash $0 enter > /dev/null 2> /dev/null
Clearing Windows version back to default
Enable sound
Creating server wrapper command in /home/adraesh/bin/sapi_server.sh
Creating Ivona voice download command in /home/adraesh/bin/ivona_download.sh
Running server


Now the output of a CRTL C on the never end script sapiconfig -n :

> 
^CTraceback (most recent call last):
  File "/usr/bin/sapiconfig", line 185, in <module>
    getVoices(sock)
  File "/usr/bin/sapiconfig", line 111, in getVoices
    a=f.readline()
  File "/usr/lib/python2.7/socket.py", line 447, in readline
    data = self._sock.recv(self._rbufsize)
KeyboardInterrupt


Again, everything works very great before the ubuntu system upgrade.

Thank you in advance.

---

### Post by frytek on 2014-08-17
Hi, jacquin.t,

please edit the 

/usr/bin/install_sapi_server

and change the display=:20 to display=:0 

(you will need sudo for this)

this is the simplest method to see what the script is actually doing. (you can use vncviewer connected to display :20 if you know how to do it). on my system it appeared that while being run, wine wants first to download some .net and gecko components, and these unexpected dialog boxes make the script freeze. use your mouse to install them - this is needed only once. you will probably need to run the script again, but this time the installation should go as usual. 

once you succeed you will probably want to change display to :20 to run the script in the background next time. 

i checked one newly-downloaded demo voice (august 2014) and it worked (although it took a considerable time to run and looked as frozen).

so i guess there will be no problems with this system for a while (until some newer versions are released again...).

---

### Post by jacquin.t on 2014-08-17
Hello frytek !

Thank you very much for your answer.

I edited the display value from 20 to 0 and run the install_sapi_server -f script, here the output :

> 
Changing current directory to /usr/lib/sapi4linux
2 Ivona voices found
No Infovox3 demo voices found
Screen already exists
299:Shutdown OK:
Shutting down wine
wine: created the configuration directory '/home/adraesh/.winesapi'
wine: configuration in '/home/adraesh/.winesapi' has been updated.
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
Setting Windows version to win2k
Clearing Windows version back to default
Disable sound
Installing ivona_voices/celine.dat
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
Installing ivona_voices/salli.dat
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
Ivona voices installed, reinstalling sapi
Setting Windows version to win2k
/usr/bin/install_sapi_server: line 101:  9557 Terminated              /bin/bash $0 enter > /dev/null 2> /dev/null
Clearing Windows version back to default
Enable sound
Creating server wrapper command in /home/adraesh/bin/sapi_server.sh
Creating Ivona voice download command in /home/adraesh/bin/ivona_download.sh
Running server


But again after that when I run the sapiconfig -n or -s the script always freeze ...

And for sapilektor always : No SAPI voices declared

Thank you again.

---

### Post by frytek on 2014-08-17
we're speaking about GUI here, but i thought i could paste a command line for producing decent mp3 files with sapilektor. 

this is basically what i use: 

cat "text.txt" | tr "&#8211;" "," | sapilektor -a -r -s 1.2 -b 1.0 -p 1.0  -v sapi_voice_name  - | \
	sox -t raw -e signed-integer -c 1 -r 22050 -b 16 - -t wav - vol 1 bass -30 treble -15 contrast 90 2>/dev/null | \
	lame --verbose --preset cbr 56 -r -m m -s 22050 - "filename.mp3"


tr is used because ivona reads "-" out loud as "dash"...

speed, pause and breath are up to you, of course.

as you can see i use sox to remove most of the advertised quality of the voices. it's a matter of personal taste; i just don't like bass because it makes the text less understandable. from the other hand: treble produces hiss that i don't like either. i have volume parameter, too, but the value of 1 changes absolutely nothing. contrast is a nice filter to try. you can skip the treble/bass/contrast/volume filters but you will probably still need sox to convert the sapilektor output to something that lame can work with. 

and you can, of course, use some more decent preset than cbr. files made with presets voice and mw-us are quite good for speech.

---

### Post by jacquin.t on 2014-08-17
I forgot to say that my environment is ubuntu SERVER.

Usually the command I use to generate my mp3 is :

cat "test.text" | sapilektor -a -r -s "1.0" -p "1.0" -v "celine" - | sox -t raw -e signed-integer -c 1 -r 22050 -b 16 - -t wav - vol "1.0" bass "0" treble "0" contrast "0" | lame --preset voice -r -m m -s 22050 - "test.mp3"

---

