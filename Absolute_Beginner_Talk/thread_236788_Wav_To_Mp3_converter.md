---
title: "Wav To Mp3 converter?"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by calvinthomas on 2006-08-15
Ok, I can find many tools that rip cds to different formats but I have files on my harddisk (they are recordings from lectures) that are in .wav and obviously the file size is huge, does anyone know a tool for converting these preferably for mp3 (they are for my brother and he is on windows) but even to a different small format supported by windows would be useful. Also I would prefer it if it were a not a command line script, if this is the only way can somebody provide me with very simple step-by-step instructions, i'm not so hot at the terminal yet!

Calv

---

### Post by nephish on 2006-08-15
i use audacity to do all my audio stuff, its really cool.
use the package manager, or in a terminal type
sudo apt-get install audacity.
the trick is, do a google to see how to get the mp3 libraries installed in ubuntu, as they are not by default. i think if you have universe available in your /etc/apt/sources.list then you could get it by installing lame. but i am not 100% on that one.

---

### Post by calvinthomas on 2006-08-15
That worked great I had to install the liblame-dev package to locate the required file but it worked fantastic, is there a way of getting audacity to do more that one at a time? Like a batch convert?

Calv

---

### Post by zba78 on 2006-08-15
You can use the package called **lame**. You simply open a terminal and type ```
lame file.wav newfile.mp3
```

Have a look at [http://lame.sourceforge.net/USAGE](http://lame.sourceforge.net/USAGE) for a guide on commands (or just type **lame --help**)

---

### Post by nephish on 2006-08-15
i dont know of a way to use audacity to batch convert.
there are lots of command line tools for this though.

glad i could help

---

### Post by benuski on 2006-08-15
SoundKonverter is my personal favorite for file converters, and it can do as many as you want at a time.  It is a KDE app, but it works much better than the Gnome SoundConverter that I'm never going to use that one again.

---

### Post by calvinthomas on 2006-08-15
I have that and at first it seemed ok but now when I put a .wav in it, it says the file format is not supported!

Calv

---

### Post by jrb114 on 2006-08-15
Hi,

Just a quick forethought, do you have to use mp3? Can you not use oggvorbis, and hence support open formats etc? If you can, you will want to use oggenc, which will (should) already be installed on your ubuntu system

Anyway, proceeding with mp3 for now...

Probably the clearest way to do this is with lame. As far as I know, there isn't a nice front end for it, but you can copy the attached script to ~/.gnome2/nautilus-scripts/ and when you right click a .wav file in nautilus, you'll have the option to convert it to a .mp3 file. Sound ok?

If so, you need to install lame. (You'll only need to do this once, and may already have it installed.)

Firstly, you need to check you have multiverse enabled in your sources.list

```

cat /etc/apt/sources.list | grep multiverse

```

You should hopefully get a line that looks like this:

```

deb http://archive.ubuntu.com/ubuntu dapper multiverse

```

If there's a # at the beginning of the line, or you don't get anything, you need to add this line to the end of your sources.list

```

sudo gedit /etc/apt/sources.list

```

And add the line to the end of the file, or uncomment it (remove the # at the beginning) if it's already there. Now we need to update the repositories information.

```

sudo apt-get update

```

And now we can install lame, phew...
```

sudo apt-get install lame

```

Now we have lame, it's nice and easy to convert .wav files to .mp3. If you type:

```

lame --help

```

You get an output that includes this:

```

RECOMMENDED:
    lame -h input.wav output.mp3

```

Which looks simple enough. Now we just need to save the attached file and put it in the correct folder. Save it to the desktop, and then execute these two lines.

```

cp ~/Desktop/wav2mp3.txt ~/.gnome2/nautilus-scripts/wav2mp3
chmod +x ~/.gnome2/nautilus-scripts/wav2mp3

```

Now, when you view the mp3 files in nautilus, you can right click them, choose "Scripts" and select "wav2mp3". This will produce an mp3 file from the wav file with the same name. 

Hope this works...

---

### Post by calvinthomas on 2006-08-16
Thankyou, if I were doing it for me i'd use ogg, I find it a better format anyway, but its for my brother and he's in windows so I don't think he can play ogg easily can he? (He only has windows media player)

Calv

---

### Post by Cagey on 2006-08-16
For ripping CDs I find Grip very useful

Oops, didn't read question properly.

Not a very 'helpful' first post....

---

### Post by ComplexNumber on 2006-08-16
> **calvinthomas said:**
> Ok, I can find many tools that rip cds to different formats but I have files on my harddisk (they are recordings from lectures) that are in .wav and obviously the file size is huge, does anyone know a tool for converting these preferably for mp3 (they are for my brother and he is on windows) but even to a different small format supported by windows would be useful. Also I would prefer it if it were a not a command line script, if this is the only way can somebody provide me with very simple step-by-step instructions, i'm not so hot at the terminal yet!

Calv
gnormalize is good for your purpose. its a gnome frontend to normalize.


> **Cagey said:**
> For ripping CDs I find Grip very useful

Oops, didn't read question properly.

Not a very 'helpful' first post....
it is helpful :). grip is a great application for many things audio.

---

### Post by calvinthomas on 2006-08-17
gnormalize was immaculate, thankyou!

Calv

---

