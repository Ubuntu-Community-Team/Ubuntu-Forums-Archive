---
title: "VEDICS Speech Assistant"
date: 2010-07-07
forum: Assistive Technology &amp; Accessibility
---

### Post by rao.nischal on 2010-07-07
VEDICS (Voice Enabled Desktop Interaction and Control System)  is an   assistive software which lets the user to interact with the OS  using   voice commands. VEDICS makes use of Sphinx 4 for doing speech   recognition and hence inherits the cool feature of user-independence.   That’s right!!! No training is required to use VEDICS!!
 VEDICS lets you do the following with your system:
 
[LIST]
[*]Perform common window operations like close, minimize, maximize etc.
[*]Invoke default applications like browsers, mail clients etc.
[*]Access any element on the desktop just by saying its name.
[/LIST]
We'll be adding the feature of dictation soon.

For more details visit: [http://vedics.sourceforge.net/](http://vedics.sourceforge.net/)

The beta version of VEDICS is now available for download at [http://sourceforge.net/projects/vedics/](http://sourceforge.net/projects/vedics/)

Please give us feedback about your experience using VEDICS. This would help us in improving it.

For demos of VEDICS visit the channel: [http://www.youtube.com/user/bharatj7](http://www.youtube.com/user/bharatj7)

Thanks.
VEDICS Team

---

### Post by rflores2323 on 2010-07-10
this is great.  I am looking for something like this to be able to control my home theater pc with xbmc ([www.xbmc.org](www.xbmc.org)).  Couple of questions.  

I see that you are able to open applications however are you able to open any application of just the default applications in ubuntu?  I want to be able to open xbmc application up

Are you able to control an application by putting a voice command to a key command (keyboard emulation)?  

also are you able to make custom commands? For instance making a prefix to be able to make sure the pc only hears the command when you say the prefix.  For instance you say "jabba open xbmc" and it opens the application.  But if you say open xbmc it does not do anything unless you give a special command like "jabba listen" so that it just listens to all your commands until another command is given. 

basically take a look at this program that is currently freeware but only works on win7 [http://voxcommando.com/](http://voxcommando.com/)
this app is really doing a great job of integrating with xbmc.  

I am sure that you would get many followers from the xbmc community as its a large community and your software can really be added to it with the new add on plugin system they are developing. take a look at the forums and go to the linux forums as there are tons and tons of users.

---

### Post by rao.nischal on 2010-07-11
currently VEDICS supports only some default applications (browser, mail, text editor, terminal and help). For rest of the applications, you can navigate in the gnome panel to get to your application. If your application is gtk based, then you can access everything within that application.

VEDICS supports only some key commands (enter, escape, home end etc). We plan to provide full keyboard support soon.

hmm.. custom commands is a nice idea. Again we will try to get that in the next release.

---

### Post by Automat2 on 2010-07-21
Watching the youtube video, you can think that for people like me, who have a strong foreign English accent, the voice recognition by the software would be difficult. It happens several times on the video.

I remember when I used Dragon, had the feature of "learning your voice", so it facilitated the "understanding" of your voice by the software. Is that present on Vedics?

---

### Post by rao.nischal on 2010-07-31
Yes, it might be slightly difficult to do perfect speech recognition with a strong accent. VEDICS is expected to work well with US English accent (since VEDICS makes use of Sphinx 4). However, you may have noticed in the videos that the speaker's accent isn't what you'd call a US English accent. And still it works to some extent (may be with a lower performance). All this happens due to the limitation that VEDICS uses Sphinx as speech to text converter. 

VEDICS currently makes use of Sphinx4 (it is still beta) as the speech-to-text converter. As far as I know no other speech-to-text converter for Linux provides as good a performance as Sphinx does. One of the objectives of Sphinx is to make speech recognition speaker independent. They have tried making it as independent as possible however it still needs a lot of improvement. 

To make a perfect speech-to-text converter, very good acoustic models are needed.And to get reliable acoustic models lot of speech samples are needed. One way in which you can help building a reliable speech recognition system is by donating your speech. You can do it online at: [http://www.voxforge.org/home/read](http://www.voxforge.org/home/read)

The more speech samples the better. So donate as much speech samples as possible so that you get performance in speech recognition.

Sphinx currently doesn't make use of "learning your voice" feature (because they are trying to make speech recognition speaker independent).

---

### Post by dansan on 2010-08-09
> **rao.nischal said:**
> VEDICS (Voice Enabled Desktop Interaction and Control System)  ...

We'll be adding the feature of dictation soon.

...
VEDICS Team

This is great news, Rao. Lack of speech recognition in linux, specifically dictation, has been the only deal breaker for me to switch my translation business entirely to Ubuntu.

I would gladly donate time to help with this project, for example, in providing speech samples (American English) for the language model or documentation.

Best regards and thanks,
Daniel

---

### Post by dansan on 2010-08-09
> **rao.nischal said:**
> ...
To make a perfect speech-to-text converter, very good acoustic models are needed.And to get reliable acoustic models lot of speech samples are needed. One way in which you can help building a reliable speech recognition system is by donating your speech. You can do it online at: [http://www.voxforge.org/home/read](http://www.voxforge.org/home/read)...

I can't get the above web page to display the recording applet. I'm running Lucid Lynx with FF with all variations of java installed. FF Advanced Preferences has Enable Java Scripts ticked.

Any clues about what's wrong?

---

### Post by rao.nischal on 2010-08-10
you need to have java plugin for firefox to run the applet.

---

### Post by dansan on 2010-08-12
> **rao.nischal said:**
> you need to have java plugin for firefox to run the applet.

Thanks for this tip, Rao. After following it, I get the applet to open but still no joy because when I click a Record button, the Java applet displays a message, saying I don't have permission to record. 

```
java.security.AccessControlException: access denied
(javax.sound.sampled.AudioPermission record)
```

So far I have found some solutions calling for adding code to .java.policy, but I haven't found out how to do this, so I asked for help in the Multimedia & Video Forum.

Meanwhile, on my Windows 7 box I have none of these problems. So, I've posted some speech samples using it. I gather from discussion on that site that 15 minutes of samples is a useful contribution. Is that right?

---

### Post by rao.nischal on 2010-08-13
Thank you very much for submitting speech sample. Any amount of speech sample submitted is always better than nothing. :)

---

### Post by scadiforever on 2010-11-28
Why Sphinx instead of Julius is used?

Thanks!

---

### Post by tenach on 2010-12-16
Interesting. I think I will be following the development of VEDICS. :)

---

### Post by UndiFineD on 2010-12-17
This is really cool,
I have been looking at the screencasts.
There some bugs though,
Is there a launchpad page ?

---

### Post by jacky.alcine on 2010-12-17
No, I was looking for that when I stumbled upon VEDICS.

See for yourself ;)
[https://launchpad.net/+search?field.text=vedics](https://launchpad.net/+search?field.text=vedics)

I've spent days and nights now looking for perfect open-source alternatives in speech recognition, and all of them have their issues.

If they (somehow) merge, though, something tells me there wouldn't be so much of a problem. Julius has a BSD license and under Clause 4; it's anchoring it from having the code (re)distributed easily.

---

### Post by rao.nischal on 2011-07-12
After quite a long gap, VEDICS-beta-0.4 has been released now. This delay is because we have been re-writing most part of the code in  python. This move from C to python was done so that the new version  VEDICS is compatible with GNOME 3. From next release onwards, we would  make regular releases of VEDICS.

After 9 months of re-coding and refactoring work, VEDICS-beta-0.4 is finally here.
 Some of the key features of this release are:
 
[LIST]
[*]**Compatibility**: VEDICS is now compatible with Old  Gnome (2.xx), Unity interface of Ubuntu as well as GNOME 3. (The dash  and the launcher of GNOME 3 and Unity are still not accessible through  VEDICS. But we have provided a new feature, as explained in the next  point, that would serve as a temporary alternative to the dash and the  launcher).
[*]**Run any application installed in the system (Launcher)**:  This is an entirely new feature that we have introduced as part of the  new VEDICS. User can start any application installed in the system by  saying “run” followed by the **full name** of the application (This acts as an alternative to the launcher).
[*]**Show names of all applications installed in the system (The Dash)**:  The user can see the full names of all the applications installed in  the system by saying the command “Show all applications”. This can then  be used to invoke any application installed in the system (This acts as  an alternative to the dash).
[*]**New UI**: VEDICS now uses notifications to tell users what command was recognized.
[*]**Bug fixes**: The complete re-writing of the code to python revealed some bugs in the code which have now been fixed.
[*]**Default Applications not supported**: Since the user  can now run any application installed in the system, we no longer  support running default applications in VEDICS-beta-0.4.
[/LIST]
For details of run applications feature watch [Demo of run applications in VEDICS-0.4]("http://www.youtube.com/watch?v=R2WpX85v9mk"). VEDICS-beta-0.4 can be downloaded from [Files]("http://sourceforge.net/projects/vedics/") section in the sourceforge page. Any suggestion/feedback is highly appreciated.

---

### Post by realn on 2011-07-26
Hi,

 Your work seems easy to use and efficient. I still have a MAJOR problem - I am using KDE3 as a DE and it seems that you program is bound to Gnome.
Is this the case? How can I make use of your wonderful program under KDE? Please, help me, I am waiting for a long time for a voice control software, and it seems that I am stuck again.
Thank you!

---

### Post by rao.nischal on 2011-07-26
I am afraid it will not work on KDE since this software makes use of Gnome specific libraries. I hope some day these libraries become compatible with KDE so that we don't have to recode our application for KDE.

---

### Post by Syndicalist on 2011-09-05
Any chance of a deb file that can be installed on Ubuntu or Mint Debian?

---

### Post by spider_0k on 2011-09-05
> **realn said:**
> Hi,

 Your work seems easy to use and efficient. I still have a MAJOR problem - I am using KDE3 as a DE and it seems that you program is bound to Gnome.
Is this the case? How can I make use of your wonderful program under KDE? Please, help me, I am waiting for a long time for a voice control software, and it seems that I am stuck again.
Thank you!

Should you wish to run Gnome software under/on KDE, you can install the relevant Gnome libraries and vice versa.

---

### Post by rao.nischal on 2011-09-06
@Syndicalist. Currently we don't have .deb files (due to lack of resources and time, we couldn't get it done). We do have a simple .sh installer that you can use (We will be most happy if somebody could help us with the .deb files)

---

### Post by bth73 on 2011-10-29
I've just finished installing, and it is hearing wrong? I say "scroll up", and it thinks I said "view". 
What is wrong and how to fix please?

---

### Post by happyyasu09 on 2011-10-29
Okeys, i did managed to install it lol. But i have two questions.
1) Why it's installed in my home directory? Oo
2) On start it says this: runtime error: could not find activate registry (and not starting of course)
I have ubuntu 11.10 with unity.
Will give more additional info, if needed, just tell me what that should be. a little bit noobie in linux. lol

---

### Post by rao.nischal on 2011-11-07
Hi Happyyasu09,

1. VEDICS is not installed in the HOME directory. It is installed in /usr/bin and /usr/lib/VEDICS. Only a few configuration files are kept in home directory in .VEDICS folder.

2. Is the accessibility feature turned on? If not please turn it on and let me know if it works or not.

By the way, which version of VEDICS did you install?

---

### Post by dadexix86 on 2012-03-16
Hi!

I just installed it today and have done a bit of bug-searching.

I'm on Ubuntu 11.10 with Gnome-Shell.

Actually if you use the recommended [FONT="Courier New"]python-pyatspi[/FONT] instead of the installed-by-default [FONT="Courier New"]python-pyatspi2[/FONT] you get the annoying
```
RuntimeError: Could not find or activate registry
```

But if you use [FONT="Courier New"]python-pyatspi2[/FONT] you'll get the annoying ```
ImportError: could not import gobject (error was: ImportError('When using gi.repository you must not import static modules like "gobject". Please change all occurrences of "import gobject" to "from gi.repository import GObject".',))

```
which will be corrected by adding ```
import gi
from gi.repository import GObject
``` to > /usr/local/lib/python2.7/dist-packages/pyVEDICS/vedics.py

Ok, we are quite there. At this time I got
```
UnboundLocalError: local variable 'accessibleList' referenced before assignment
```
which I solved by using this script (from a comment on the project page)
```
import dbus
try :
  _bus = dbus.SessionBus()
  _proxy = _bus.get_object("org.a11y.Bus", "/org/a11y/bus")
  _desktopProps = dbus.Interface(_proxy, dbus_interface='org.freedesktop.DBus.Properties')
  isAtspi2 = True
except:
  import gconf
  isAtspi2 = False

if isAtspi2 :
  _desktopProps.Set('org.a11y.Status', 'IsEnabled', True)
else :
  cl = gconf.client_get_default()
  cl.set_bool('/desktop/gnome/interface/accessibility', True)
```
now there are two big problems:
1) I have to run this script everytime I launch vedics, otherwise I'll get the local variable error.
2) It doesn't work, because it says
```
vedics 
/usr/lib/python2.7/dist-packages/gobject/constants.py:24: Warning: g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
  import gobject._gobject
start
end
10:08.102 CONFIG logMath            Log base is 1.0001
10:08.122 CONFIG logMath            Using AddTable when adding logs
10:08.122 CONFIG logMath            LogAdd table has 99022 entries.
10:08.303 INFO microphone           Desired format: PCM_SIGNED 16000.0 Hz, 16 bit, mono, 2 bytes/frame, big-endian supported.
event
10:08.327 CONFIG wsjLoader          Loading Sphinx3 acoustic model: etc/WSJ_clean_13dCep_16k_40mel_130Hz_6800Hz.4000.mdef
10:08.327 CONFIG wsjLoader              modellName: etc/WSJ_clean_13dCep_16k_40mel_130Hz_6800Hz.4000.mdef
10:08.328 CONFIG wsjLoader              dataDir   : cd_continuous_8gau/
event
10:08.477 INFO unitManager          CI Unit: *+AH+
10:08.481 INFO unitManager          CI Unit: *+BREATH+
10:08.482 INFO unitManager          CI Unit: *+CLICK+
10:08.482 INFO unitManager          CI Unit: *+GRUNT+
10:08.483 INFO unitManager          CI Unit: *+NOISE+
10:08.483 INFO unitManager          CI Unit: *+RING+
10:08.483 INFO unitManager          CI Unit: *+SLAM+
10:08.484 INFO unitManager          CI Unit: *+SMACK+
10:08.484 INFO unitManager          CI Unit: *+TONE+
10:08.485 INFO unitManager          CI Unit: AA
10:08.485 INFO unitManager          CI Unit: AE
10:08.486 INFO unitManager          CI Unit: AH
10:08.486 INFO unitManager          CI Unit: AO
10:08.486 INFO unitManager          CI Unit: AW
10:08.487 INFO unitManager          CI Unit: AY
10:08.487 INFO unitManager          CI Unit: B
10:08.488 INFO unitManager          CI Unit: CH
10:08.488 INFO unitManager          CI Unit: D
10:08.488 INFO unitManager          CI Unit: DH
10:08.489 INFO unitManager          CI Unit: EH
10:08.489 INFO unitManager          CI Unit: ER
10:08.490 INFO unitManager          CI Unit: EY
10:08.490 INFO unitManager          CI Unit: F
10:08.490 INFO unitManager          CI Unit: G
10:08.491 INFO unitManager          CI Unit: HH
10:08.491 INFO unitManager          CI Unit: IH
10:08.492 INFO unitManager          CI Unit: IY
10:08.492 INFO unitManager          CI Unit: JH
10:08.493 INFO unitManager          CI Unit: K
10:08.493 INFO unitManager          CI Unit: L
10:08.493 INFO unitManager          CI Unit: M
10:08.494 INFO unitManager          CI Unit: N
10:08.494 INFO unitManager          CI Unit: NG
10:08.495 INFO unitManager          CI Unit: OW
10:08.495 INFO unitManager          CI Unit: OY
10:08.496 INFO unitManager          CI Unit: P
10:08.496 INFO unitManager          CI Unit: R
10:08.496 INFO unitManager          CI Unit: S
10:08.497 INFO unitManager          CI Unit: SH
10:08.498 INFO unitManager          CI Unit: T
10:08.498 INFO unitManager          CI Unit: TH
10:08.498 INFO unitManager          CI Unit: UH
10:08.499 INFO unitManager          CI Unit: UW
10:08.499 INFO unitManager          CI Unit: V
10:08.500 INFO unitManager          CI Unit: W
10:08.500 INFO unitManager          CI Unit: Y
10:08.500 INFO unitManager          CI Unit: Z
10:08.501 INFO unitManager          CI Unit: ZH
10:08.597 INFO wsjLoader            ModelLoader
10:08.598 INFO wsjLoader            Pool cd_continuous_8gau/means Entries: 33176
10:08.598 INFO wsjLoader            Pool cd_continuous_8gau/variances Entries: 33176
10:08.598 INFO wsjLoader            Pool cd_continuous_8gau/transition_matrices Entries: 49
10:08.598 INFO wsjLoader            Pool senones Entries: 4147
10:08.598 INFO wsjLoader            Pool meanTransformationMatrix Entries: 1
10:08.598 INFO wsjLoader            Pool meanTransformationMatrix Entries: 1
10:08.599 INFO wsjLoader            Pool varianceTransformationMatrix Entries: 1
10:08.599 INFO wsjLoader            Pool varianceTransformationMatrix Entries: 1
10:08.599 INFO wsjLoader            Pool cd_continuous_8gau/mixture_weights Entries: 4147
10:08.599 INFO wsjLoader            Pool senones Entries: 4147
10:08.599 INFO wsjLoader            Context Independent Unit Entries: 49
10:08.599 INFO wsjLoader            HMM Manager: 110878 hmms
10:08.600 INFO wsj                  CompositeSenoneSequences: 0
10:08.600 INFO dictionary           Loading dictionary from: file:/tmp/VEDICS/edu/cmu/sphinx/model/acoustic/WSJ_8gau_13dCep_16k_40mel_130Hz_6800Hz/dict/cmudict.0.6d
10:08.603 INFO dictionary           Loading filler dictionary from: file:/tmp/VEDICS/edu/cmu/sphinx/model/acoustic/WSJ_8gau_13dCep_16k_40mel_130Hz_6800Hz/dict/fillerdict
WARNING: Grammar missing self identifying header
10:08.699 WARNING dictionary        Missing word: terminale
10:08.699 WARNING jsgfGrammar       Can't find pronunciation for terminale
10:08.699 WARNING dictionary        Missing word: cerca
10:08.699 WARNING jsgfGrammar       Can't find pronunciation for cerca
10:08.700 WARNING dictionary        Missing word: modifica
10:08.700 WARNING jsgfGrammar       Can't find pronunciation for modifica
10:08.700 WARNING dictionary        Missing word: visualizza
10:08.700 WARNING jsgfGrammar       Can't find pronunciation for visualizza
10:08.700 WARNING dictionary        Missing word: aiuto
10:08.700 WARNING jsgfGrammar       Can't find pronunciation for aiuto
10:08.703 INFO jsgfGrammar          Num nodes : 569
10:08.703 INFO jsgfGrammar          Num arcs  : 770
10:08.704 INFO jsgfGrammar          Avg arcs  : 1.3532513
10:08.473 INFO microphone           Final format: PCM_SIGNED 16000.0 Hz, 16 bit, mono, 2 bytes/frame, big-endian
10:08.478 INFO microphone           open
10:08.489 INFO microphone           line listener Open event from line com.sun.media.sound.DirectAudioDevice$DirectTDL@1b7e189
10:08.493 INFO microphone           Frame size: 320 bytes
10:08.509 INFO microphone           started recording
10:08.511 INFO microphone           DataStartSignal added
10:08.515 INFO microphone           line listener Start event from line com.sun.media.sound.DirectAudioDevice$DirectTDL@1b7e189
genrating dict
done genrating dict
WARNING: Grammar missing self identifying header
10:08.768 WARNING dictionary        Missing word: terminale
10:08.769 WARNING jsgfGrammar       Can't find pronunciation for terminale
10:08.769 WARNING dictionary        Missing word: cerca
10:08.770 WARNING jsgfGrammar       Can't find pronunciation for cerca
10:08.770 WARNING dictionary        Missing word: modifica
10:08.770 WARNING jsgfGrammar       Can't find pronunciation for modifica
10:08.771 WARNING dictionary        Missing word: visualizza
10:08.771 WARNING jsgfGrammar       Can't find pronunciation for visualizza
10:08.771 WARNING dictionary        Missing word: aiuto
10:08.771 WARNING jsgfGrammar       Can't find pronunciation for aiuto
10:08.773 INFO jsgfGrammar          Num nodes : 569
10:08.774 INFO jsgfGrammar          Num arcs  : 770
10:08.774 INFO jsgfGrammar          Avg arcs  : 1.3532513

# --------------- Summary statistics ---------
   Total Time Audio: 0,00s  Proc: 0,00s  Speed: 0,00 X real time
10:08.776 INFO dictionary           Loading dictionary from: file:/tmp/VEDICS/edu/cmu/sphinx/model/acoustic/WSJ_8gau_13dCep_16k_40mel_130Hz_6800Hz/dict/cmudict.0.6d
10:08.779 INFO dictionary           Loading filler dictionary from: file:/tmp/VEDICS/edu/cmu/sphinx/model/acoustic/WSJ_8gau_13dCep_16k_40mel_130Hz_6800Hz/dict/fillerdict
10:08.813 INFO jsgfGrammar          Num nodes : 569
10:08.814 INFO jsgfGrammar          Num arcs  : 770
10:08.814 INFO jsgfGrammar          Avg arcs  : 1.3532513
1
Sending 1
event
event
```
but when I try to speak it doesn't say me anything.

Any suggestions?

---

### Post by rao.nischal on 2012-03-17
Hi,

Please try adjusting your mic.

As for the other problems, it will be fixed in vedics-0.5

---

### Post by dadexix86 on 2012-03-17
Ok, after a shoutdown the situation now is this:
```
$ vedics 
/usr/lib/python2.7/dist-packages/gobject/constants.py:24: Warning: g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
  import gobject._gobject
start
end
WARNING: Grammar missing self identifying header
WARNING: Grammar missing self identifying header

# --------------- Summary statistics ---------
   Total Time Audio: 0,00s  Proc: 0,00s  Speed: 0,00 X real time
1
event
event
```

The mic is working fine with Cheese, Skype and GoogleTalk.

Vedics, simply ignores what I say.

Are there more informations I can provide?

---

### Post by rao.nischal on 2012-03-17
Hi dadexix86,

Its not a matter about whether the mic is working fine or not. There are many things that come into picture when speech is processed by software like background noise, accent etc. What appears as normal speech for us (when we, say, record sound and replay it or hear it on skype) may appear as distorted speech  to software. So adjusting the mic so that speech recognition works fine is necessary.

A good way to adjust the mic would be to open the sound settings and check the mic input level. If the mic is detecting sounds even when you are not speaking then it means that there is lot of (white) noise around. Reduce the mic input level such that the mic input level changes only when you speak.

There is also a way to make speech recognition work in noisy environment. I haven't tested it and so I cannot guarantee you success. But if it works do let me know. 

Replace the file /usr/lib/VEDICS/vedics.config.xml with the following:

```

<?xml version="1.0" encoding="UTF-8"?>

<!-- ******************************************************** -->
<!--  an4 configuration file                             -->
<!-- ******************************************************** -->

<config>

    <!-- ******************************************************** -->
    <!-- frequently tuned properties                              -->
    <!-- ******************************************************** -->

    <property name="logLevel" value="CONFIG"/>

    <property name="absoluteBeamWidth"  value="-1"/>
    <property name="relativeBeamWidth"  value="1E-80"/>
    <property name="wordInsertionProbability" value="1E-36"/>
    <property name="languageWeight"     value="8"/>

    <property name="frontend" value="epFrontEnd"/>
    <property name="recognizer" value="recognizer"/>
    <property name="showCreations" value="false"/>


    <!-- ******************************************************** -->
    <!-- word recognizer configuration                            -->
    <!-- ******************************************************** -->

    <component name="recognizer" type="edu.cmu.sphinx.recognizer.Recognizer">
        <property name="decoder" value="decoder"/>
        <propertylist name="monitors">
            <item>accuracyTracker </item>
            <item>speedTracker </item>
            <item>memoryTracker </item>
        </propertylist>
    </component>

    <!-- ******************************************************** -->
    <!-- The Decoder   configuration                              -->
    <!-- ******************************************************** -->

    <component name="decoder" type="edu.cmu.sphinx.decoder.Decoder">
        <property name="searchManager" value="searchManager"/>
    </component>

    <component name="searchManager"
        type="edu.cmu.sphinx.decoder.search.SimpleBreadthFirstSearchManager">
        <property name="logMath" value="logMath"/>
        <property name="linguist" value="flatLinguist"/>
        <property name="pruner" value="trivialPruner"/>
        <property name="scorer" value="threadedScorer"/>
        <property name="activeListFactory" value="activeList"/>
    </component>


    <component name="activeList"
             type="edu.cmu.sphinx.decoder.search.PartitionActiveListFactory">
        <property name="logMath" value="logMath"/>
        <property name="absoluteBeamWidth" value="${absoluteBeamWidth}"/>
        <property name="relativeBeamWidth" value="${relativeBeamWidth}"/>
    </component>

    <component name="trivialPruner"
                type="edu.cmu.sphinx.decoder.pruner.SimplePruner"/>

    <component name="threadedScorer"
                type="edu.cmu.sphinx.decoder.scorer.ThreadedAcousticScorer">
        <property name="frontend" value="${frontend}"/>
         <property name="isCpuRelative" value="true"/>
 <property
    name="numThreads" value="2"/>
 <property name="minScoreablesPerThread" value="50"/>
 <property
    name="scoreablesKeepFeature" value="true"/>
 </component>

    <!-- ******************************************************** -->
    <!-- The linguist  configuration                              -->
    <!-- ******************************************************** -->

    <component name="flatLinguist"
                type="edu.cmu.sphinx.linguist.flat.FlatLinguist">
        <property name="logMath" value="logMath"/>
        <property name="grammar" value="jsgfGrammar"/>
        <property name="acousticModel" value="wsj"/>
        <property name="wordInsertionProbability"
                value="${wordInsertionProbability}"/>
        <property name="languageWeight" value="${languageWeight}"/>
        <property name="unitManager" value="unitManager"/>
    </component>


    <!-- ******************************************************** -->
    <!-- The Grammar  configuration                               -->
    <!-- ******************************************************** -->

    <component name="jsgfGrammar" type="edu.cmu.sphinx.jsapi.JSGFGrammar">
        <property name="dictionary" value="dictionary"/>
        <property name="grammarLocation"
             value="resource:/vedics!/vedics/"/>
        <property name="grammarName" value="vedics"/>
    <property name="logMath" value="logMath"/>
    </component>


    <!-- ******************************************************** -->
    <!-- The Dictionary configuration                            -->
    <!-- ******************************************************** -->

    <component name="dictionary"
        type="edu.cmu.sphinx.linguist.dictionary.FastDictionary">
        <property name="dictionaryPath"
     value="resource:/edu.cmu.sphinx.model.acoustic.WSJ_8gau_13dCep_16k_40mel_130Hz_6800Hz.Model!/edu/cmu/sphinx/model/acoustic/WSJ_8gau_13dCep_16k_40mel_130Hz_6800Hz/dict/cmudict.0.6d"/>
        <property name="fillerPath"
     value="resource:/edu.cmu.sphinx.model.acoustic.WSJ_8gau_13dCep_16k_40mel_130Hz_6800Hz.Model!/edu/cmu/sphinx/model/acoustic/WSJ_8gau_13dCep_16k_40mel_130Hz_6800Hz/dict/fillerdict"/>
        <property name="addSilEndingPronunciation" value="false"/>
        <property name="allowMissingWords" value="true"/>
        <property name="unitManager" value="unitManager"/>
    </component>

    <!-- ******************************************************** -->
    <!-- The acoustic model configuration                         -->
    <!-- ******************************************************** -->
    <component name="wsj"
      type="edu.cmu.sphinx.model.acoustic.WSJ_8gau_13dCep_16k_40mel_130Hz_6800Hz.Model">
        <property name="loader" value="wsjLoader"/>
        <property name="unitManager" value="unitManager"/>
    </component>

    <component name="wsjLoader"
               type="edu.cmu.sphinx.model.acoustic.WSJ_8gau_13dCep_16k_40mel_130Hz_6800Hz.ModelLoader">
        <property name="logMath" value="logMath"/>
        <property name="unitManager" value="unitManager"/>
    </component>


    <!-- ******************************************************** -->
    <!-- The unit manager configuration                           -->
    <!-- ******************************************************** -->

    <component name="unitManager"
        type="edu.cmu.sphinx.linguist.acoustic.UnitManager"/>

    <!-- ******************************************************** -->
    <!-- The frontend configuration                               -->
    <!-- ******************************************************** -->

    <component name="frontEnd" type="edu.cmu.sphinx.frontend.FrontEnd">
        <propertylist name="pipeline">
            <item>microphone </item>
            <item>preemphasizer </item>
            <item>windower </item>
            <item>fft </item>
            <item>melFilterBank </item>
            <item>dct </item>
            <item>liveCMN </item>
            <item>featureExtraction </item>
        </propertylist>
    </component>

    <!-- ******************************************************** -->
    <!-- The live frontend configuration                          -->
    <!-- ******************************************************** -->
    <component name="epFrontEnd" type="edu.cmu.sphinx.frontend.FrontEnd">
        <propertylist name="pipeline">
            <item>microphone </item>
            <item>dataBlocker </item>
            <item>speechClassifier </item>
            <item>speechMarker </item>
            <item>nonSpeechDataFilter </item>
            <item>preemphasizer </item>
            <item>windower </item>
            <item>fft </item>
           <item>wiener</item>
            <item>melFilterBank </item>
            <item>dct </item>
            <item>liveCMN </item>
            <item>featureExtraction </item>
        </propertylist>
    </component>

    <!-- ******************************************************** -->
    <!-- The frontend pipelines                                   -->
    <!-- ******************************************************** -->

    <component name="dataBlocker" type="edu.cmu.sphinx.frontend.DataBlocker">
        <!--<property name="blockSizeMs" value="10"/>-->
    </component>

    <component name="speechClassifier"
               type="edu.cmu.sphinx.frontend.endpoint.SpeechClassifier">
        <property name="threshold" value="13"/>
    </component>

    <component name="nonSpeechDataFilter"
               type="edu.cmu.sphinx.frontend.endpoint.NonSpeechDataFilter"/>

    <component name="speechMarker"
               type="edu.cmu.sphinx.frontend.endpoint.SpeechMarker" >
        <property name="speechTrailer" value="50"/>
    </component>


    <component name="preemphasizer"
               type="edu.cmu.sphinx.frontend.filter.Preemphasizer"/>

    <component name="windower"
               type="edu.cmu.sphinx.frontend.window.RaisedCosineWindower">
    </component>

    <component name="fft"
            type="edu.cmu.sphinx.frontend.transform.DiscreteFourierTransform">
    </component>

    <component name="melFilterBank"
        type="edu.cmu.sphinx.frontend.frequencywarp.MelFrequencyFilterBank">
    </component>

    <component name="dct"
            type="edu.cmu.sphinx.frontend.transform.DiscreteCosineTransform"/>

    <component name="liveCMN"
               type="edu.cmu.sphinx.frontend.feature.LiveCMN"/>

    <component name="featureExtraction"
               type="edu.cmu.sphinx.frontend.feature.DeltasFeatureExtractor"/>

    <component name="microphone"
               type="edu.cmu.sphinx.frontend.util.Microphone">
        <property name="closeBetweenUtterances" value="false"/>
    </component>


    <!-- ******************************************************* -->
    <!--  monitors                                               -->
    <!-- ******************************************************* -->

    <component name="accuracyTracker"
                type="edu.cmu.sphinx.instrumentation.BestPathAccuracyTracker">
        <property name="recognizer" value="${recognizer}"/>
        <property name="showAlignedResults" value="false"/>
        <property name="showRawResults" value="false"/>
    </component>

    <component name="wiener"  
        type="edu.cmu.sphinx.frontend.endpoint.WienerFilter">
        <property name="classifier" value="speechClassifier"/>
    </component>

    <component name="memoryTracker"
                type="edu.cmu.sphinx.instrumentation.MemoryTracker">
        <property name="recognizer" value="${recognizer}"/>
    <property name="showSummary" value="false"/>
    <property name="showDetails" value="false"/>
    </component>

    <component name="speedTracker"
                type="edu.cmu.sphinx.instrumentation.SpeedTracker">
        <property name="recognizer" value="${recognizer}"/>
        <property name="frontend" value="${frontend}"/>
    <property name="showSummary" value="true"/>
    <property name="showDetails" value="false"/>
    </component>


    <!-- ******************************************************* -->
    <!--  Miscellaneous components                               -->
    <!-- ******************************************************* -->

    <component name="logMath" type="edu.cmu.sphinx.util.LogMath">
        <property name="logBase" value="1.0001"/>
        <property name="useAddTable" value="true"/>
    </component>

</config>


```For details visit: [http://nsh.nexiwave.com/2010/02/noise-reduction-filtering-in-sphinx4.html](http://nsh.nexiwave.com/2010/02/noise-reduction-filtering-in-sphinx4.html)

---

### Post by dadexix86 on 2012-03-17
Ok, I think that the problem does not depend on Vedics.

In fact, if I let the mic volume on "Not amplified" no sound at all is recorded by any application.
But, when I let it up a bit, until I can hear it, a lot of noise shows up. This noise is automatically reduced by GTalk but is not reduced, as an example, by Skype or Cheese.

I have not thought that the problem should be this. I'll investigate it, because this noise is really annoying and, moreover, it shows up both with the integrated mic and with an external one, so I think that's not hardware-related.

Many, many thanks.

---

