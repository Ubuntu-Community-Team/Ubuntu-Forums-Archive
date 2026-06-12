---
title: "Need program for BATCH conversion mp3-&gt;wave &amp; vice versa"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-09-07
I'm running Ubuntu 7.04 (feisty) and need a program to do bulk i.e. batch conversion from mp3 to wave, and from wave to mp3. Is there a program that will do this for me?

i.e. if I have 50 files and want to convert all at the same time. So for this, the Audacity application will not serve the purpose. There should be a program for batch conversion of multiple files at once, that will do the work without first importing each file to show the wave form, as Audacity does.

---

### Post by AusIV4 on 2007-09-07
I've not used it myself, but I believe soundconverter has a batch mode.

sudo aptitude install sound converter

or search for it in Add / Remove Programs.

---

### Post by justleen on 2007-09-07
lame can do conversion on a commandline
```
#!/bin/bash

for  files in `ls  -1 /dir/to/musicfile` ; do
   noextension=$(echo $files| sed -e 's/.mp3//' -e 's/.MP3//')
   lame $files " $noextension".wav
done


```

---

### Post by swarup on 2007-09-07
If Soundconverter can do batch conversion, then that will be the best thing. I'd far prefer the convenience of a GUI. I'm loading Add/Remove programs now, and I'll try and see if it has the batch facility. If it does, then that will be wonderful. -- Yes, I just finished downloading it and I opened the application. It looks from the appearance like it is made for batch conversion. Thanks so much! 

> **justleen said:**
> lame can do conversion on a commandline
```
#!/bin/bash

for  files in `ls  -1 /dir/to/musicfile` ; do
   noextension=$(echo $files| sed -e 's/.mp3//' -e 's/.MP3//')
   lame $files " $noextension".wav
done


```

Could you explain a bit more in English as to how to use the above code? I would certainly use it if I needed to, but just let me know a bit more as to how I plug in my specific info into the code there. For example, if I have a folder of 50 mp3 files, then do I just put the pathway to that folder in where you have "/dir/to/musicfile"? And it will convert all 50 files as a batch?

And how do I alter the code if I want to go from wave to mp3 versus mp3 to wave?

---

### Post by mridkash on 2007-09-07
It is a shell script.

Copy the code into the text editor and replace the dir/to/musicfile with the path of a folder where you keep your mp3s. 

And save the file as mp3converter.sh in home folder or somewhere. 

Now right click on the mp3converter.sh file and select properties, go to permissions tab and tick mark the execute check box.

Now you need to have lame installed, go to synaptic manager and search for lame. install it.

now just populate the music folder you specified with mp3 files and then dbl click on mp3converter.sh and select run in terminal. See what happens!

---

### Post by swarup on 2007-09-07
> **mridkash said:**
> It is a shell script.

Copy the code into the text editor and replace the dir/to/musicfile with the path of a folder where you keep your mp3s. 

And save the file as mp3converter.sh in home folder or somewhere. 

Now right click on the mp3converter.sh file and select properties, go to permissions tab and tick mark the execute check box.

Now you need to have lame installed, go to synaptic manager and search for lame. install it.

now just populate the music folder you specified with mp3 files and then dbl click on mp3converter.sh and select run in terminal. See what happens!

That sounds really nice. I will do it. 

Now, this is a process I guess for converting mp3 to wave, right?

Will the program also convert wave to mp3? If so, what does one have to change in order for that to be done?

And one last question: When you "dbl click on mp3converter.sh and select run in terminal", is it that the effect of "dbl click on mp3converter.sh" is going to be to have a terminal window automatically open?  And then in that terminal window something will appear there where I can select "run" ?

---

### Post by mridkash on 2007-09-11
double clicking on the mp3converter.sh will bring up a window displaying 4 options
run in terminal
display
cancel
run

if u select run in terminal, a terminal window opens and starts executing the script, u dont need to do anything else.

if u want a wave converter
make some changes to the script, replace all mp3 with wav and wav with mp3 in the script.
I guess this should work, try this on a sample folder to see.

---

### Post by vanadium on 2007-09-11
I am afraid that the current script will try to encode an mp3 file to an mp3 file with a wav extenstion. It will work (a compressed file will be produced), but don't play it: may break your equipment and ears.

To decode, you need to supply the --decode option:

lame --decode <mp3file> 

Thus, the relevant script line should read

lame --decode $files "$noextension.wav"

The "noextension" trick is nice, but ou could also use "basename" to strip off the .mp3 part from the file name.

---

### Post by clubsoda on 2007-11-20
The funny thing is, if you run lame without specifying the output file, it simply adds ".mp3" to the end, so you get filenames like BeBop.wav.mp3.  Wouldn't it have been nice if lame automatically replaced the extension, then you could specify multiple input files and we wouldn't be having this discussion.  :)

Anyway, here's my attempt based on the helpful posts above.  I call it **laminate**, for converting a bunch of wav files to mp3:-```
#!/bin/bash

for  files in `ls  -1 *.wav` ; do
   bn=`basename $files .wav`
   lame -ms --noreplaygain --vbr-new -V0 $files $bn.mp3
done

```Save this as "laminate", make it executable with chmod +x, then sudo copy it to /usr/local/bin so that it's in your path for executables.  Then change directory to wherever your wavs are located and simply **laminate** them.

---

