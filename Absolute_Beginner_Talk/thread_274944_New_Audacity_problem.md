---
title: "New Audacity problem"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by ricardisimo on 2006-10-10
Hey everyone,
     I've finally gotten *Audacity* to convert my m4as to mp3s, but it's converting them exactly the same way it's playing them: at hyper-speed. All of the songs sound like a sneeze from a bionic munchkin. The Help files point me to the "Effect > Change Speed", but this option is not present for me... almost no options are present, in fact. Any clues here? TIA.

---

### Post by Perfect Storm on 2006-10-10
Is it a compiled version you use? If so make sure the right -dev libs are installed before compiling it.

---

### Post by ricardisimo on 2006-10-10
> **Artificial Intelligence said:**
> Is it a compiled version you use? If so make sure the right -dev libs are installed before compiling it.

I have no idea what that means, unfortunately. For whatever it's worth, the "About" on Audacity give me no info whatsoever. There's just a button that say "Audacious!" Where do I find out what I'm working with, and where do i get libs?

---

### Post by Perfect Storm on 2006-10-10
compile means that you build the application from the source.

You can read more here: [http://audacity.sourceforge.net/](http://audacity.sourceforge.net/) or [http://audacity.sourceforge.net/download/source](http://audacity.sourceforge.net/download/source)

---

### Post by ricardisimo on 2006-10-10
> **Artificial Intelligence said:**
> compile means that you build the application from the source.

You can read more here: [http://audacity.sourceforge.net/](http://audacity.sourceforge.net/) or [http://audacity.sourceforge.net/download/source](http://audacity.sourceforge.net/download/source)

I've got whatever version one gets via "Add/Remove Applications". Which one is that? "About" isn't telling me anything.

---

### Post by Zimmer on 2006-10-10
> **ricardisimo said:**
> Hey everyone,
     I've finally gotten *Audacity* to convert my m4as to mp3s, but it's converting them exactly the same way it's playing them: at hyper-speed. All of the songs sound like a sneeze from a bionic munchkin. The Help files point me to the "Effect > Change Speed", but this option is not present for me... almost no options are present, in fact. Any clues here? TIA.

Not present or greyed out?

Some menu items are grayed out or disabled until they are ready for use. Before choosing an effect, you must select the audio that you want to change. To select audio, click and drag with the Selection tool to highlight it, or choose the “Select All” command from the Edit menu.

SOme great resource for Audacity here
[http://audacity.sourceforge.net/help/](http://audacity.sourceforge.net/help/)
and here
[http://www-users.york.ac.uk/~raa110/audacity/AudacityHelp.html](http://www-users.york.ac.uk/~raa110/audacity/AudacityHelp.html)

---

### Post by ricardisimo on 2006-10-10
It was in fact greyed out, and after tinkering, that was clearly not the issue. There's something much more basic going on... it's not reading audio files properly. Back to square one.

By the way, all I want is to be able to burn audio CDs. I need either a way to convert audio files to formats that GnomeBaker or Serpentine can use, or I need plugins for GnomeBaker and/or Serpentine to allow them to work with any and all formats. I have had zero luck with either approach. Has anyone else had this dilemma, and what course would they recommend? Thanks again.

---

### Post by Artemis3 on 2006-10-10
As far as i know, Audacity does not handle .m4a. Most likely these files are Advanced Audio Coding (AAC) files encapsulated inside .m4a, as Apple likes to do.

Now you need something that can read those files and convert them to something else, like .wav or .mp3

I think mplayer can do this very nicely.
Once you install mplayer, open a terminal and use a command line like this:

```
mplayer -ao pcm inputfile.m4a -ao pcm:file="outfile.wav"
```

This will turn your file into .wav that can be burned by any cd program.

---

### Post by ricardisimo on 2006-10-11
> **Artemis3 said:**
> As far as i know, Audacity does not handle .m4a. Most likely these files are Advanced Audio Coding (AAC) files encapsulated inside .m4a, as Apple likes to do.

Now you need something that can read those files and convert them to something else, like .wav or .mp3

I think mplayer can do this very nicely.
Once you install mplayer, open a terminal and use a command line like this:

```
mplayer -ao pcm inputfile.m4a -ao pcm:file="outfile.wav"
```

This will turn your file into .wav that can be burned by any cd program.

I want you to know that this marks a grand occasion for me. This is the very first problem I've had within Ubuntu that I've actually solved (this is not quite true; it's the first problem I've solved that I didn't cause myself). Thank you very, very much for the help here Artemis3. I can even feel a little bit good about my own brain, since it wouldn't work until I got all of the syntax right, got the file location right (god bless drag-n-drop), dropped the spaces out of the file name and lost the comma in the song title, etc., etc., ...

Quick question: What does "pcm" stand for? I couldn't find it in the help files and I'll never learn or remember any of this if I can't translate it into something resembling Spanglish. Thanks again.

---

### Post by Joey French on 2006-10-11
I have not tried to burn music in that particular format, but I can tell you this: K3b is without a doubt the greatest burning software in the linux universe. I would not be surprised if it was able to burn this type of file with a simple drag and drop. 

/Yes, I try to big up K3b whenever possible. It's that good. One of the linux apps that truly "just works"./

Joey

---

### Post by Zimmer on 2006-10-12
> **ricardisimo said:**
> ... ...

Quick question: What does "pcm" stand for? I couldn't find it in the help files and I'll never learn or remember any of this if I can't translate it into something resembling Spanglish. Thanks again.

Pulse Code Modulation. Turns analog sound into digital sound. Looks like the technique for converting a file using MPlayer 'plays' the file and records the output in a digital form, rather than using an algorithm to re-code it.

---

### Post by ricardisimo on 2006-10-12
> **Zimmer said:**
> Pulse Code Modulation. Turns analog sound into digital sound. Looks like the technique for converting a file using MPlayer 'plays' the file and records the output in a digital form, rather than using an algorithm to re-code it.

Curious. Seems like an odd way of doing it. How does this work quality-wise? Am I losing much info? Should I work with the resulting wav file for burning, or can I convert it to a smaller file and work with that reasonably well in the future? Thanks.

---

### Post by ricardisimo on 2006-10-12
> **Joey French said:**
> I have not tried to burn music in that particular format, but I can tell you this: K3b is without a doubt the greatest burning software in the linux universe. I would not be surprised if it was able to burn this type of file with a simple drag and drop. 

/Yes, I try to big up K3b whenever possible. It's that good. One of the linux apps that truly "just works"./

Joey

I'm going to have to take your word on it, because my very first impression of it was that it not only can't work m4as, it also can't work mp3s, which is an absolute first for me in either Ubuntu or Windows. Now, I'm certain that this is a quick fix with a plugin, but I've already expended WAAAYYYY too much energy on burning one single, solitary cd to have to worry about whether K3B is worth the effort. One day I'll check it out. Thanks.

---

### Post by Zimmer on 2006-10-13
> **ricardisimo said:**
> It was in fact greyed out, and after tinkering, that was clearly not the issue. There's something much more basic going on... it's not reading audio files properly. Back to square one.

By the way, all I want is to be able to burn audio CDs. I need either a way to convert audio files to formats that GnomeBaker or Serpentine can use, or I need plugins for GnomeBaker and/or Serpentine to allow them to work with any and all formats. I have had zero luck with either approach. Has anyone else had this dilemma, and what course would they recommend? Thanks again.

When creating CD's (from recordings made in Audacity) I export to .wav format, which is acceptable to Gnomebaker. Are you still suffering from the hyper speed issue, though ?
From what I have searched the MPlayer method is the only quick way of converting this format, and the site showing the earlier method posted here shows this little script for converting all files in a directory

#!/bin/bash
# 
# m4a2wav
# 
for i in *.m4a; do
    out=$(echo $i | sed -e 's/.m4a//g')
    mplayer -ao pcm "$i" -ao pcm:file="$out.wav"
done


Here is the link 
[http://gimpel.gi.funpic.de/wiki/index.php?title=Howto:convert_aac/mp4_to_wav/mp3/ogg_on_Linux](http://gimpel.gi.funpic.de/wiki/index.php?title=Howto:convert_aac/mp4_to_wav/mp3/ogg_on_Linux)

and this link may be of interest,too
[http://badcomputer.org/unix/dir2ogg/](http://badcomputer.org/unix/dir2ogg/)

---

### Post by ricardisimo on 2006-10-13
> **Zimmer said:**
> Are you still suffering from the hyper speed issue, though ?

No, that problem was, I'm assuming, exactly what was said earlier... *Audacity* has no idea what to do with m4as, hence the munchkin sneeze. Thanks for the other info.

---

