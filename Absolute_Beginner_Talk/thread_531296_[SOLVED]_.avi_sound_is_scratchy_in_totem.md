---
title: "[SOLVED] .avi sound is scratchy in totem"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by lledurt on 2007-08-21
I am having a problem playing my .avi files in totem on my edbuntu 7.04 machine (dell 4600c)  they work fine on my other computer.  

 I thought it might be a sound card configuration issue, but I had luck playing them with gxine.  

 It is not a network issue because I copied it locally and played it without any change.

 Is there a  configuration file that I am missing or a plug-in?

 I have installed the m32 codecs and the gstreamer ffmpeg.

 I see there are 2 other threads similar to this with no responses.  Thanks for your help.


P.J.

---

### Post by ddrichardson on 2007-08-21
How is audio configured in totem options

---

### Post by lledurt on 2007-08-22
Problem Solved, but I don't know why

The preferences were the same on totem for audio,  both were set to stereo but that did not help.

Here is what solved it.

In each home directory the file ~/.gconf/apps/totem/%gconf.xml there is an audio line.

                     <entry name="audio_output_type" mtime="1187792432" type="int" value="0">

I noticed that the mtime values for my computer that was working was different then the one that wasn't so I did the following on the computer that was not working:

                   cd /.gconf/apps/totem
                   mv %gconf.xml %gconf.xml.old

                  scp [email]user@workingcomputer:/home/user/.gconf/apps/totem/%gconf.xml[/email] .
                                  user is an user account working on working computer
                                  working computer is the ip address of the working computer

                 I then restarted totem and it worked.

Here is what I don't understand.  After running totem again, the mtime value on the audio entry changed to mtime="1187792432" which is different than the value in the file I copied in.  

I checked everything else in the files between the new and the old and they seemed the samd besides the mtime values.  Go figure.

The good news is that it works.  I had to change it in all the users directories so it worked for all the users.

Thanks for your help.  

P.J.

---

### Post by ddrichardson on 2007-08-22
Great - mark the thread as solved so that others with the same problem can benefit from it.

---

### Post by lledurt on 2008-04-22
I have another computer with this same problem and the above did not help, but this did.  I thought I would add this to help.

Edit>Preferences>Audio TAB>   I chose AC3 Passthrough

My first machine uses 5.1-channel and works great.

I guess you need to try everything.

Now that I am starting to use cinelerra, I am learning quite a bit about sample rates/frame rates/ and sound and video in general.  Which is the problem.  AVI sound does not import well into cinelerra because of this(same is true with the video) so I either convert first or let cinelerra do it.

Totem is very powerful and can play things that windows and mac reject outright.

P.J.

---

