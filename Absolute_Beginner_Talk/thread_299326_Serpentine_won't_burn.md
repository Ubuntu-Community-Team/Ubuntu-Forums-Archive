---
title: "Serpentine won't burn"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by cactaur on 2006-11-14
When I want to burn my CD and press the burn button, I get a message that says "Converting Files Failed" then "Writing to disc didn't start so it is still usable." My playlist contains 16 mp3s and they should be able to fit on my CD, can anyone see what's wrong? Thank you.

---

### Post by sunexplodes on 2006-11-14
The thing that we, as former-windows users take for granted is the fact that, before being burned to cd, mp3s must be converted to wav files, which most windows apps do on their own.

I'd reccomend fishing around for a package in synaptic that would allow that kind of conversion. After a quick search, I found one called mp3burn which could be what you're looking for.

---

### Post by cactaur on 2006-11-14
Ok, I installed mp3burn, but unfortunately, for some reason, it can't read the .m3u playlist I made. I tried looking in the ubuntu packages, but I couldn't find one like it. Maybe I should try looking on the internet as a last resort. It says Serpentine should be able to burn mp3s. Should I try submitting a bug, or is there a better way?

---

### Post by sunexplodes on 2006-11-14
Have you tried burning the mp3s themselves, instead of using the m3u file?

---

### Post by cactaur on 2006-11-14
Well, yes, but if I burn one mp3, won't that render the disk unwritable after that?

---

### Post by sunexplodes on 2006-11-14
Well, don't just burn ONE mp3, drag SEVERAL mp3s into the Serpentine window.

---

### Post by cactaur on 2006-11-14
Wait, I thought we were talking about mp3burn. I have no problem setting up mp3s in Serpentine, but I'll try putting multiple files in the terminal. Heh, I guess you can do that, well, I'll let you know how it turns out.

---

### Post by cactaur on 2006-11-14
Ok, I burned it with mp3burn, but when I played it, it seemed to be compressed quite heavily. It's like a chipmunk is singing some my songs. Cool, but not quite what I wanted.

EDIT: Do you think Serpentine can't convert for a reason, I'll try compiling to 0.7 and see what happens.

---

### Post by Bill Statler on 2006-11-21
> **cactaur said:**
> When I want to burn my CD and press the burn button, I get a message that says "Converting Files Failed" then "Writing to disc didn't start so it is still usable."...

I had the same thing happen today.  Apparently it's a real software bug, but it's easy to fix with a text editor.

The bug is documented [here]("https://launchpad.net/distros/ubuntu/+bug/22501"), and the fix is about halfway down the page where it says "THE FIX". ;) 

Here's how to do it.  This worked for me using Serpentine version 0.6.91-0ubuntu3.

1: Probably best to make sure Serpentine isn't running.

2: Edit this file (using sudo or logged in as root):
```
sudo gedit /usr/lib/python2.4/site-packages/serpentine/audio.py
```

3: Go to line 495.  It should read:
```
"audioconvert ! "
```
Change it to:
```
"audioconvert ! audioresample !"
```
Make sure you don't change the indenting, because Python cares about that.

4: Save the file, and try running Serpentine.

NOTE: This is ONLY a fix for the bug that causes the error message "Converting files failed: Writing to disc didn't start so it is still usable."  If you are having some different Serpentine problem, this probably won't fix it.

I don't understand the code well enough to know *why* this works, but it did work for me, and let me burn some MP3's onto an audio CD which was playable on my old CD player.  I suppose the edited audio.py file will get overwritten by the next update, but hopefully by then the bug will be fixed.

---

### Post by Busch on 2006-11-24
THANKS!!! above poster it worked for me :)

---

### Post by sgarman on 2006-11-26
Bill, your post is very much appreciated! This also fixed the issue for me with Serpentine not decoding some mp3s. I've had this problem as far back as Dapper. If you're ever in Southern NH, I owe you a beer. :)

Regards,

Scott

---

### Post by ntense on 2006-11-26
so i tried this fix and it didnt work.... are there any other ideas for this out there?

---

### Post by killaray on 2006-12-28
> **Bill Statler said:**
> I had the same thing happen today.  Apparently it's a real software bug, but it's easy to fix with a text editor.

The bug is documented [here]("https://launchpad.net/distros/ubuntu/+bug/22501"), and the fix is about halfway down the page where it says "THE FIX". ;) 

Here's how to do it.  This worked for me using Serpentine version 0.6.91-0ubuntu3.

1: Probably best to make sure Serpentine isn't running.

2: Edit this file (using sudo or logged in as root):
```
sudo gedit /usr/lib/python2.4/site-packages/serpentine/audio.py
```

3: Go to line 495.  It should read:
```
"audioconvert ! "
```
Change it to:
```
"audioconvert ! audioresample !"
```
Make sure you don't change the indenting, because Python cares about that.

4: Save the file, and try running Serpentine.

NOTE: This is ONLY a fix for the bug that causes the error message "Converting files failed: Writing to disc didn't start so it is still usable."  If you are having some different Serpentine problem, this probably won't fix it.

I don't understand the code well enough to know *why* this works, but it did work for me, and let me burn some MP3's onto an audio CD which was playable on my old CD player.  I suppose the edited audio.py file will get overwritten by the next update, but hopefully by then the bug will be fixed.

great fix.. worked perfectly

---

### Post by Space Age Whiz Kid on 2007-03-14
It worked for me also. Strangely, last time I installed Dapper, I didn't need to make this edit. Serpentine worked fine creating cds from mp3s. :confused:

---

### Post by undertakingyou on 2007-03-14
> **ntense said:**
> so i tried this fix and it didnt work.... are there any other ideas for this out there?

You could try K3B to do the burning.  It is a KDE app but will run in the gnome environment with just a couple of libraries.  I use it for all my burning.

---

### Post by H.E. Pennypacker on 2007-03-14
Bill's guide worked for me.

---

### Post by rosswmcgee on 2007-04-18
> **Bill Statler said:**
> I had the same thing happen today.  Apparently it's a real software bug, but it's easy to fix with a text editor.

The bug is documented [here]("https://launchpad.net/distros/ubuntu/+bug/22501"), and the fix is about halfway down the page where it says "THE FIX". ;) 

Here's how to do it.  This worked for me using Serpentine version 0.6.91-0ubuntu3.

1: Probably best to make sure Serpentine isn't running.

2: Edit this file (using sudo or logged in as root):
```
sudo gedit /usr/lib/python2.4/site-packages/serpentine/audio.py
```

3: Go to line 495.  It should read:
```
"audioconvert ! "
```
Change it to:
```
"audioconvert ! audioresample !"
```
Make sure you don't change the indenting, because Python cares about that.

4: Save the file, and try running Serpentine.

NOTE: This is ONLY a fix for the bug that causes the error message "Converting files failed: Writing to disc didn't start so it is still usable."  If you are having some different Serpentine problem, this probably won't fix it.

I don't understand the code well enough to know *why* this works, but it did work for me, and let me burn some MP3's onto an audio CD which was playable on my old CD player.  I suppose the edited audio.py file will get overwritten by the next update, but hopefully by then the bug will be fixed.
I have the same problem with Serpentine. Did the Sudo find no line 495 or any other numbered lines. So I used synaptic and installed K3b. It worked perfectly. However when I played the CD made from an MP file there was no sound.

---

### Post by Bill Statler on 2007-04-22
> **rosswmcgee said:**
> I have the same problem with Serpentine. Did the Sudo find no line 495 or any other numbered lines. So I used synaptic and installed K3b. It worked perfectly. However when I played the CD made from an MP file there was no sound.

Sorry, I should have been more clear.  *There are no numbered lines in audio.py* -- what I meant is, go to the 495th line in the file, and make the change. 

A text editor ought to show you what line you're on -- in gedit, the default Ubuntu text editor, it's down in the bottom-right, and there's also a "Go to Line..." function under the Search menu.

I don't know whether this has been fixed in a more recent version of Serpentine.  I'm still using Ubuntu 6.06 Dapper and Serpentine 0.6.91-0ubuntu3 here.

Sorry I can't help with your K3B problems.  Good luck!

---

### Post by Pikestaff on 2007-08-30
> **Bill Statler said:**
> I had the same thing happen today.  Apparently it's a real software bug, but it's easy to fix with a text editor.

The bug is documented [here]("https://launchpad.net/distros/ubuntu/+bug/22501"), and the fix is about halfway down the page where it says "THE FIX". ;) 

Here's how to do it.  This worked for me using Serpentine version 0.6.91-0ubuntu3.

1: Probably best to make sure Serpentine isn't running.

2: Edit this file (using sudo or logged in as root):
```
sudo gedit /usr/lib/python2.4/site-packages/serpentine/audio.py
```

3: Go to line 495.  It should read:
```
"audioconvert ! "
```
Change it to:
```
"audioconvert ! audioresample !"
```
Make sure you don't change the indenting, because Python cares about that.

4: Save the file, and try running Serpentine.

NOTE: This is ONLY a fix for the bug that causes the error message "Converting files failed: Writing to disc didn't start so it is still usable."  If you are having some different Serpentine problem, this probably won't fix it.

I don't understand the code well enough to know *why* this works, but it did work for me, and let me burn some MP3's onto an audio CD which was playable on my old CD player.  I suppose the edited audio.py file will get overwritten by the next update, but hopefully by then the bug will be fixed.

Huge thanks, I was having this issue on Kubuntu Dapper (yeah, I use the Gnome CD Burner :p ) and this fixed it perfectly, thank you!

---

### Post by newagelink on 2008-03-09
Why is it when I run ```
sudo gedit /usr/lib/python2.4/site-packages/serpentine/audio.py
```in the terminal, gedit opens a *blank file*? And then when I try to exit, it asks me if I want to save the changes I've made ... as if it's opening the file, and then erasing everything to a blank page. And I'm copy/pasting that code. What the heck?!

I've navigated to /usr/lib/python2.4/site-packages -- I guess using Nautilus? -- and there is no /serpentine folder. Could that be why I'm having this issue? If so, then where is this /serpentine/audio.py file in Ubuntu 7.10?

---

### Post by halitech on 2008-03-09
try changing it to 

```
sudo gedit /usr/lib/python2.5/site-packages/serpentine/audio.py
```

---

### Post by newagelink on 2008-03-09
Right, thanks: I found that file and after a cursory glance thought it wasn't the right one. It might be, but I'm not sure what to do if it is: I found the following: ```
################################################################################
def source_to_wav(source, sink):
    """
    Converts a given source element to wav format and sends it to sink element.
    
    To convert a media file to a wav using gst-launch:
    source ! decodebin ! audioconvert ! audioresample ! audioconvert ! wavenc
    """
    
    bin = gst.parse_launch(
        "decodebin name=stw_decodebin ! audioconvert ! "
        "audioresample ! audioconvert ! %s ! wavenc name=stw_wavenc" % _WAV_PCM_PARSE
    )
    
    oper = GstOperation(sink, bin)
      
    decoder = bin.get_by_name("stw_decodebin")
    encoder = bin.get_by_name("stw_wavenc")

    oper.bin.add(source)
    oper.bin.add(sink)
    source.link(decoder)
    encoder.link(sink)
    
    return oper

source_to_wav = operations.operation_factory(source_to_wav)

def convert_to_wav(source, source_location, sink_location):
    """
    Utility function that given a source filename it converts it to a wav
    with sink_filename.
    """
    sink = safe_element_factory_make("filesink")
    sink.set_property("location", sink_location)
    return source_to_wav(create_source(source, source_location), sink)

convert_to_wav = operations.operation_factory(convert_to_wav)
convert_to_wav = operations.async(convert_to_wav)

commands = {
    "convert": convert_to_wav,
    "is_wav": is_wav_pcm,
    "get_metadata": get_metadata
}


```That doesn't seem to match the scenario from the first page -- the text to add is already present.

---

### Post by tenjin1 on 2008-06-12
> **newagelink said:**
> Right, thanks: I found that file and after a cursory glance thought it wasn't the right one. It might be, but I'm not sure what to do if it is: I found the following: ```
################################################################################
def source_to_wav(source, sink):
    """
    Converts a given source element to wav format and sends it to sink element.
    
    To convert a media file to a wav using gst-launch:
    source ! decodebin ! audioconvert ! audioresample ! audioconvert ! wavenc
    """
    
    bin = gst.parse_launch(
        "decodebin name=stw_decodebin ! audioconvert ! "
        "audioresample ! audioconvert ! %s ! wavenc name=stw_wavenc" % _WAV_PCM_PARSE
    )
    
    oper = GstOperation(sink, bin)
      
    decoder = bin.get_by_name("stw_decodebin")
    encoder = bin.get_by_name("stw_wavenc")

    oper.bin.add(source)
    oper.bin.add(sink)
    source.link(decoder)
    encoder.link(sink)
    
    return oper

source_to_wav = operations.operation_factory(source_to_wav)

def convert_to_wav(source, source_location, sink_location):
    """
    Utility function that given a source filename it converts it to a wav
    with sink_filename.
    """
    sink = safe_element_factory_make("filesink")
    sink.set_property("location", sink_location)
    return source_to_wav(create_source(source, source_location), sink)

convert_to_wav = operations.operation_factory(convert_to_wav)
convert_to_wav = operations.async(convert_to_wav)

commands = {
    "convert": convert_to_wav,
    "is_wav": is_wav_pcm,
    "get_metadata": get_metadata
}


```That doesn't seem to match the scenario from the first page -- the text to add is already present.
Same here. The text to add is already present and is on line 521. I am usinf Serpentine 0.7 btw

---

### Post by thomascj on 2008-07-11
i'm in the same boat as the previous two posts -- anyone have any other idea's?

---

