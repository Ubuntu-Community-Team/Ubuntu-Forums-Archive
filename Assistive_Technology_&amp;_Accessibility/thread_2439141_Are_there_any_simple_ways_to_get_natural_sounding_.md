---
title: "Are there any simple ways to get natural sounding text-to-speech on Linux?"
date: 2020-03-23
forum: Assistive Technology &amp; Accessibility
---

### Post by adrian-dickenson on 2020-03-23
I'm a releative newbie to Linux and Ubuntu with a visual impairment who really wants to make a full break from Windows, but can't because the text-to-speech options are just so awful.

Over the years I've grown used to using a number of voices on Windows (from AT& T, ScanSoft, Microsoft and others) at speeds that most people find indecipherable, but I just can't find any native Linux ones that come anywhere close to them.  

Searching this site and others shows either quite old instructions for the ghastly espeak voices - or the slightly better Festival ones - or relatively complicated options of setting up WINE options.  

Setting these up on Windows was a doddle - can anyone point me to any help that might make it so on Linux?

FYI - I don't need a full screen-reader, just the ability to select text and have it read back to me with a short-cut key.

Any advice gratefully received.

---

### Post by TheFu on 2020-03-23
No.
I found a relatively easy way to convert text to speech, but the resulting audio files are just too mechanical. It is a 100% native Linux solution, since I won't use WINE.   

```
#!/bin/bash
# Dependencies:
#  sudo apt install libttspico-utils festival festvox-us-slt-hts
#  sudo apt install ./festvox-us-slt-hts_0.2010.10.25-3_all.deb 
#  sudo apt install libttspico-utils festival
#  The .deb package is from the debian repos which should be compatible
#     with Ubuntu 16.04.  Later Ubuntus have it in their repo.

# Input file is from txt created from epub using calibre tool:
#       ebook-convert input.epub output.txt

ROOT=${1/%.txt/}

# Provided as part of the Festival TTS engine
text2wave "$1" -o "$ROOT.wav"
ffmpeg -i "$ROOT.wav"  -codec:a libmp3lame -qscale:a 6 "$ROOT.mp3"
rm "$ROOT.wav"
```

Using X11 select-paste (left mouse to select; center mouse to paste), some thing like **cat < | text2wave | mpv ** as an xdotool command might work. That's a bunch of stdin and stdout redirection. I didn't verify that text2wave or mpv support this redirection, but most shell commands do. I don't have a text2wave capable system up right now.

Perhaps this will be sufficient for someone?

---

### Post by ipv on 2020-03-23
> **adrian-dickenson said:**
> can anyone point me to any help that might make it so on Linux?

have a look here : [https://www.linuxlinks.com/speechtools/](https://www.linuxlinks.com/speechtools/)

& here : [https://blog.michaelamerz.com/wordpress/the-state-of-the-art-linux-text-to-speech-tts/](https://blog.michaelamerz.com/wordpress/the-state-of-the-art-linux-text-to-speech-tts/)

the 2nd link has some voice samples too for your convenience.

---

### Post by ipv on 2020-03-23
> **TheFu said:**
> I found a relatively easy way to convert text to speech, but the resulting audio files are just too mechanical. It is a 100% native Linux solution, since I won't use WINE.   Perhaps this will be sufficient for someone?

OP has already tried espeak & festival & is looking for something better.

---

### Post by TheFu on 2020-03-23
> **ipv said:**
> OP has already tried espeak & festival & is looking for something better.

Which is why the answer "no" was first.

However, in the next few years, someone else will find this thread and might want to see for themselves. Figured I’d make it easier for anyone else because i happened to have worked through it recently.  "No" for one person isn't necessarily no for everyone.

---

### Post by ipv on 2020-03-24
> **TheFu said:**
> However, in the next few years, someone else will find this thread and might want to see for themselves.

+1 for the optimism.

---

### Post by adrian-dickenson on 2020-03-24
> **ipv said:**
> have a look here : [https://www.linuxlinks.com/speechtools/](https://www.linuxlinks.com/speechtools/)

& here : [https://blog.michaelamerz.com/wordpress/the-state-of-the-art-linux-text-to-speech-tts/](https://blog.michaelamerz.com/wordpress/the-state-of-the-art-linux-text-to-speech-tts/)

the 2nd link has some voice samples too for your convenience.


Thanks - I'd come across those sites during my search and have approached a company recommended in the 2nd link ([https://www.cepstral.com](https://www.cepstral.com)) although they require a request via a support ticket to find out if they will supply me with a stand-alone voice and at what price.  

The others are variations on the espeak / Festival options that I've already tried (although there are a few newer festival voices that might be an improvement over the ones I've tried).  

Thanks for the advice!

---

### Post by adrian-dickenson on 2020-03-24
> **TheFu said:**
> No.
I found a relatively easy way to convert text to speech, but the resulting audio files are just too mechanical. It is a 100% native Linux solution, since I won't use WINE.   




I fear you may be right, which is a huge shame and quite a hurdle for those of us with visual problems accessing any Linux OS.  I have in the past used all sorts of voices (I've been visually impaired since 1987), but trying to move to Ubuntu with the default voices is like going back to 1995.

if I have any success I'll update this original question and answer myself below.

---

### Post by de Bacon on 2020-10-11
I too have this problem.  I used to use gespeaker, with the past two LTR's of UbuntuStudio.  I upgraded to 20.04 today, Gespeaker is no longer available?????  What are we to do?
It used to be Orca, then that quit working, with 16.04 I think(?).  I found gespeaker then kind of cumbersome, but now that didn't quit working it just disappeared from the repository.   I to am quite dependent on these kinds of software.  Ubuntu, is supposed to be for the for the better good as I recall from years back, 2008 is when I switched away from microsuck.  I will search on and tell here if I find something.

---

### Post by de Bacon on 2020-10-16
I finally figured out orca, in its current state.  To the best of my understanding, the current version lacks what one would expect as a Graphical User Interface (gui) and does have an odd sounding speech function.  Yet I have been using these "voices" so long now that I understand them easily.  I had used orca years ago, yet with an upgrade of versions of the Ubuntu, the gui vanished.  It forced one to use a terminal interface, then once I got it loaded and running, that was as far as I could get.  No instructions are provided.

Just this morning, I went to the orca website [HTML]https://help.gnome.org/users/orca/stable/introduction.html.en[/HTML]  

step 1. Load orca via software installer or synaptic, or install it via the terminal  entering the following code. ```
sudo apt install orca
```
step 2. close the terminal.
step 3. open another terminal window then, enter the following code to setup orca. ```
orca -s
```
It takes some time to figure out what the multitudes of settings actually represent.  I am sure that the Gnome help web page quoted above can be helpful with settings.  Being patient, and working through the process may bring success.  Once it is setup. I use the simple Mousepad text editor as a source for orca to read from.  Then when I find something in a webpage or a document that I want to hear, I copy it and paste into the text editor and orca reads it just fine.

Best of luck

---

### Post by xopi on 2021-03-30
**Install festival**:
Select distro in [https://pkgs.org/search/?q=festival](https://pkgs.org/search/?q=festival)
E.g. for Ubuntu 20.04 [https://ubuntu.pkgs.org/20.04/ubuntu-universe-arm64/festival_2.5.0-4build1_arm64.deb.html](https://ubuntu.pkgs.org/20.04/ubuntu-universe-arm64/festival_2.5.0-4build1_arm64.deb.html) 
In there search for: *Install Howto*  and run it:
```
    # Update the package index:
    sudo apt-get update
    # Install festival deb package:
    sudo apt-get install festival
```
If desired to install through binaries, you may check:
[https://www.cstr.ed.ac.uk/projects/festival/download.html](https://www.cstr.ed.ac.uk/projects/festival/download.html)
[http://www.festvox.org/docs/manual-2.4.0/festival_6.html#Installation](http://www.festvox.org/docs/manual-2.4.0/festival_6.html#Installation)
[https://wiki.ubuntuusers.de/Festival/](https://wiki.ubuntuusers.de/Festival/)
[https://wiki.ubuntuusers.de/Festival/Kompilieren/](https://wiki.ubuntuusers.de/Festival/Kompilieren/) --> to use german voices

Partial outdated guide to add **further voices**: [https://ubuntuforums.org/showthread.php?t=751169&highlight=festival](https://ubuntuforums.org/showthread.php?t=751169&highlight=festival) (19 pages long thread! ](*,))
E.g. use **CMU Arctic voices**
Its section "Installing the enhanced CMU Arctic voices" should be corrected [but it's closed thread] (rest of steps works for me in Ubuntu 20.04):
```
sudo mv * /usr/share/festival/voices/us/
``` 
instead of 
```
sudo mv * /usr/share/festival/voices/english/ # WRONG
```
Also specified in its *README* file:
```
$ batcat [path_to_unzip_CMU_Arctic_voice]/README
   1   &#9474; 
   2   &#9474; CMU ARCTIC AWB 0.90
   3   &#9474; 
   4   &#9474; This distrory contains a recording of the phonetically balanced US
   5   &#9474; English CMU ARCTIC database by AWB, a Scottish English speaker.
...
  53   &#9474; INSTALLING AS A FESTIVAL VOICE
  54   &#9474; ==============================
...
  73   &#9474; Or to install as voice in your Festival installation it must appear
  74   &#9474; as a subdirectory of a subdirectory of a directory listed in the 
  75   &#9474; Festival variable voice-path.  For standard installations you can
  76   &#9474; create the following directory if it doesn't exist
  77   &#9474; 
  78   &#9474;     /...WHATEVER.../festival/lib/voices/us/
```

Online test voices: [http://festvox.org/voicedemos.html](http://festvox.org/voicedemos.html)
And the whole list of voices can be checked in: [URL="http://www.speech.cs.cmu.edu/cmu_arctic/packed/"]http://www.speech.cs.cmu.edu/cmu_arctic/packed/

[/URL]

---

### Post by QIII on 2021-03-30
Good night, sweet thread.  

Requiescat in pace.

---

