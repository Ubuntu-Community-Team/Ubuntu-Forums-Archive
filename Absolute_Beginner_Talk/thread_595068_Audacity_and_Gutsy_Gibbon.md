---
title: "Audacity and Gutsy Gibbon"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by ynottony on 2007-10-28
[FONT="Book Antiqua"]Just upgraded from Feisty Fawn  to Gutsy Gibbon.

When I record something, using the mic jack, in Audacity and attempt to play it back I get this message:

"Error while opening sound device. Please check the output device settings and the project sample rate."

Had no problem recording in Audacity and playing back my recording with Feisty Fawn.

Also, when I attempt to use Audacity to record a file from my Sony Mini-disc player, I get all kinds of static and interference noise, when I input the mic jack.  I tried right-clicking on the desktop sound icon and opening Volume Control and making adjustments there, but it didn't stop the static-nterference noises.  

There is no problem when I record from the Sony mini-disc into Audacity on my  Windows PC.. Not sure what the problem is.  I love Gutsy Gibbon so far and am going through the learning curve as a Linux Newbie.

I am using a Compaq Presario x1000 laptop.  Would apprecate any help.  Thanks.

- Tony Brigmon[/FONT]

---

### Post by Palmyra on 2007-10-28
Here's what I found through a Google search:

Try opening Audacity as SUDO, using the following command:

gksudo aoss audacity

Explanation:  This opens Audacity using administrative priviliges, using AOSS (I am thinking this is OSS).  Anyhow, give it a try.  If you're having problems with GKSUDO, use SUDO (even though it's not recommended).  If it complains about AOSS, I guess you have to download and install it (use Synaptic or use sudo apt-get install aoss). 

I know it's silly to open Audacity using SUDO, but it worked for me.

---

### Post by ynottony on 2007-10-28
That fixed the playback problem after recording with a mic.  Thank you.

Playing the Sony Mini-disc player while recording  into Audacity still causes static noises.  Any thoughts on that?  It does not happen when I play and record into Audacity on my Windows PC

- Tony Brigmon

---

### Post by RockTonic3 on 2007-11-05
hm i'm having the same problem...  worked fine in previous versions and now won't work in gutsy.

i tried gksudo aoss audacity, but strangely enough it didn't give me any output at all, so i tried to run just gksudo audacity, which resulted in the same problem i was having before, but i got some (maybe?) useful output.  

check it out:
```
chris@Voltaire:~$ gksudo aoss audacity
chris@Voltaire:~$ gksudo audacity
sh: jackd: not found
Expression 'parameters->channelCount <= maxChans' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 786
Expression 'ValidateParameters( outputParameters, hostApi, StreamDirection_Out )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1781
Expression 'SetApproximateSampleRate( pcm, hwParams, sr )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1124
Expression 'PaAlsaStreamComponent_InitialConfigure( &self->capture, inParams, self->primeBuffers, hwParamsCapture, &realSr )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1675
Expression 'PaAlsaStream_Configure( stream, inputParameters, outputParameters, sampleRate, framesPerBuffer, &inputLatency, &outputLatency, &hostBufferSizeMode )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1799


```

any help is appreciated thanks!

---

### Post by tonymoloney on 2007-11-06
What version of Audacity do you have?
I've found that add/remove programs in Kubuntu gives you version 1.3.3 which is a Beta.
The stable version is 1.2.6

---

### Post by RockTonic3 on 2007-11-06
damn.  felt good about that one, but it didn't change anything.

---

### Post by rogerdean on 2007-11-12
same problem here... 

"Error while opening sound device. Please check the output device settings and the project sample rate."

any news anyone?

---

### Post by rogerdean on 2007-11-12
got it. from another thread...

'Install the alsa-oss package.
Set your Audacity output device as the OSS device. Worked for me, on Gutsy 64-bit'

---

### Post by tonymoloney on 2007-11-13
My Add/remove programs can't find also-oss.
Where to from here.

---

### Post by rogerdean on 2007-11-13
you'll need to search for it using synaptic
System->Administration->Synaptic Package Manager...

---

### Post by ubnewbie2 on 2007-11-13
spelling?  it's alsa-oss

---

### Post by ubnewbie2 on 2007-11-13
Also, why not just change the preferences to use ALSA directly?

---

