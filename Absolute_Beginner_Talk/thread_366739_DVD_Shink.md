---
title: "DVD Shink"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by Grundair on 2007-02-21
Just got DVD Shink from Automatix and it goes well until it is time to burn the DVD. HEre is the log showing the error. ANy ideas?

02/21/07 07:33:08    DVDShrink log for V_FOR_VENDETTA\n
                     Project variables
                     -----------------------------------------------

                     WDEVICE=/dev/dvd
                     RDEVICE=/dev/dvd
                     RMFILES=1
                     AUTOBURN=1
                     AUDIO=0
                     TITLE=1
                     SUBTITLE=0
                     ALANG=en
                     SLANG=en
                     PROJNAME=V_FOR_VENDETTA
                     WORKDIR=/tmp/V_FOR_VENDETTA
                     VIDEOFILE=/tmp/V_FOR_VENDETTA/V_FOR_VENDETTA.m2v
                     SHRNKFILE=/tmp/V_FOR_VENDETTA/shrunken.V_FOR_VENDETTA.m2v
                     AUDIOFILE=/tmp/V_FOR_VENDETTA/V_FOR_VENDETTA.ac3
                     SUBFILE=/tmp/V_FOR_VENDETTA/V_FOR_VENDETTA.sub
                     MPGFILE=/tmp/V_FOR_VENDETTA/V_FOR_VENDETTA.mpg
                     MUXFILE=/tmp/V_FOR_VENDETTA/muxed.mpg
                     VFIFO=/tmp/videofifo
                     AFIFO=/tmp/audiofifo
                     SFIFO=/tmp/subtitlefifo
                     CMDFILE=/tmp/dvdshrink.prog
                     VARFILE=/tmp/dvdshrink.var
                     INFOFILE=/tmp/V_FOR_VENDETTA/V_FOR_VENDETTA.info
                     ISOONLY=0
                     SHRINK=1
                     STREAMONLY=0
                     BIGSTREAMONLY=0
                     MPEGONLY=0
                     BIGMPEGONLY=0
                     RMFILES=1
                     ADDTITLES=0
                     MYSHRINK=0
                     AUTHORONLY=0
                     DELETELOGS=0
                     
                     Source DVD Selections
                     -----------------------------------------------

                     Title:                   1
                     Audio stream:            0
                     Audio language:          en
                     
                     Chapter list
                     -----------------------------------------------

                     00:00:00.000,00:02:23.667,00:09:06.833,00:10:59.333,00:16:25.499,00:21:54.699,00:24:59.366,00:30:07.499,00:35:34.665,00:40:34.332,00:43:10.999,00:47:59.332,00:49:37.332,00:54:06.199,00:56:35.532,01:00:27.165,01:04:42.532,01:09:36.032,01:12:02.665,01:18:45.831,01:21:07.665,01:25:55.831,01:29:14.831,01:32:02.164,01:36:14.864,01:39:21.997,01:44:10.697,01:48:43.330,01:51:56.496,01:53:50.196,01:57:43.863,01:59:27.496,02:04:30.662
02/21/07 07:33:11    Commenced DVD rip.
                     Video stream: /tmp/V_FOR_VENDETTA/V_FOR_VENDETTA.m2v
                     Audio stream: /tmp/V_FOR_VENDETTA/V_FOR_VENDETTA.ac3
02/21/07 07:47:25    DVD rip completed. Elapsed time [00:14:14]
                     Maximum size per title allowed:   4700000000
                     Size of elemental streams: Video: 5747922668
                                                Audio: 445279744
                                                Sub:   0
                     Calculated shrink factor:         1.41
02/21/07 07:47:25    M2V re-quantization of /tmp/V_FOR_VENDETTA/V_FOR_VENDETTA.m2v commenced. Factor 1.41
02/21/07 07:59:02    M2V re-quantization completed. Elapsed time [00:25:51]
                     New video stream size 4076217072
02/21/07 07:59:09    Re-multiplexing of /tmp/V_FOR_VENDETTA/V_FOR_VENDETTA.mpg started.
02/21/07 08:06:39    Re-multiplexing completed. Elapsed time [00:33:28]
02/21/07 08:06:48    Commenced DVD author in /tmp/V_FOR_VENDETTA/BUILD
02/21/07 08:06:48    Commenced building DVD on drive
02/21/07 08:14:18    Authoring complete. Elapsed time [00:41:07]
02/21/07 08:14:18    Commenced writing DVD TOC
02/21/07 08:14:19    TOC build completed. Elapsed time [00:41:08]
02/21/07 08:18:09    DVD burn commenced.
02/21/07 08:18:11    growisofs -speed=8 -Z /dev/dvd -dvd-video -V V_FOR_VENDETTA /tmp/V_FOR_VENDETTA/BUILD/ > /dev/null 2> /tmp/V_FOR_VENDETTA/growisofsdebug.txt failed!
                     growisofs reported an error writing the new DVD!
                     Run terminated!
                       
                     Output of debug file
                       
INFO:	UTF-8 character encoding detected by locale settings.
	Assuming UTF-8 encoded filenames on source filesystem,
	use -input-charset to override.
  0.22% done, estimate finish Wed Feb 21 08:18:10 2007
  0.44% done, estimate finish Wed Feb 21 08:21:55 2007
  0.66% done, estimate finish Wed Feb 21 08:20:40 2007
:-[ SET STREAMING failed with SK=5h/ASC=26h/ACQ=00h]: Input/output error

---

### Post by jethro10 on 2007-02-21
I can't answer your problem directly but this is what I do.

Chose the Shrink option to make an ISO.

When complete, I right click the file and the option to burn it is there.

J

---

### Post by Grundair on 2007-02-21
> **jethro10 said:**
> I can't answer your problem directly but this is what I do.

Chose the Shrink option to make an ISO.

When complete, I right click the file and the option to burn it is there.

J

Just tried that and got this:

02/21/07 08:48:28    DVD rip completed. Elapsed time [00:13:10]
                     Maximum size per title allowed:   4700000000
                     Size of elemental streams: Video: 5747922668
                                                Audio: 445279744
                                                Sub:   0
                     Calculated shrink factor:         1.41
02/21/07 08:48:28    M2V re-quantization of /tmp/V_FOR_VENDETTA/V_FOR_VENDETTA.m2v commenced. Factor 1.41
02/21/07 08:58:26    M2V re-quantization completed. Elapsed time [00:23:08]
                     New video stream size 4076217072
02/21/07 08:58:34    Re-multiplexing of /tmp/V_FOR_VENDETTA/V_FOR_VENDETTA.mpg started.
02/21/07 09:05:51    Re-multiplexing completed. Elapsed time [00:30:33]
02/21/07 09:05:51    Commenced DVD author in /tmp/V_FOR_VENDETTA/BUILD
02/21/07 09:05:51    Commenced building DVD on drive
02/21/07 09:13:57    Authoring complete. Elapsed time [00:38:39]
02/21/07 09:13:57    Commenced writing DVD TOC
02/21/07 09:13:57    TOC build completed. Elapsed time [00:38:39]
02/21/07 09:13:57    ISO file /home/V_FOR_VENDETTA.iso creation commenced.
02/21/07 09:13:58    nice -n +19 mkisofs -dvd-video -V V_FOR_VENDETTA -o /home/V_FOR_VENDETTA.iso /tmp/V_FOR_VENDETTA/BUILD/ > /dev/null 2> /tmp/V_FOR_VENDETTA/mkisodebug.txt failed!
                     mkisofs reported an error creating the ISO!
                     Run terminated!
                       
                     Output of debug file
                       
INFO:	UTF-8 character encoding detected by locale settings.
	Assuming UTF-8 encoded filenames on source filesystem,
	use -input-charset to override.
mkisofs: Permission denied. Unable to open disc image file '/home/V_FOR_VENDETTA.iso'.

---

### Post by fede on 2007-03-02
Hello, 

I don't have dvdshrink currently installed, but from what I read in the error message, it seems that it is trying to write the image to /home/v_for_vendetta.iso, that is to say, to a file in the /home directory.

Now, generally the /home directory is owned by root and the user doesn't have permission to write to it. I think this must be your problem: you should try to write the image to /home/YOUR_USER_NAME (whatever your user is, which is your home directory), or to other directory where you have permission to write to (for example, generally anything inside your home directory, by default)

I think you might have mistaken /home for your home directory. Your home directory is /home/YOUR_USER_NAME : in my box, for example, it is /home/fede/ . Check what it is in your case.

Hope it helps, and sorry if I misunderstood and this is a too obvious (and stupid suggestion).

---

### Post by orb9220 on 2007-03-02
I use dvdshrink all the time. And as fede says it is about permissions. I create a folder called movies in /home and then right click properties on folder and change the permissions to  allow me to read and write to that folder.

Then I just right-click .iso and write from nautilus.

V for Vendetta is a great flick!

---

### Post by MrKlean on 2007-03-02
ND... Make sure the folder you're writing to has enough room for the file ; )

---

### Post by jkeyes0 on 2007-03-02
try making the movies folder within your /home/username folder instead of inside /home. If you're not running the program as root (which you shouldn't be) it won't be allowed to create files/folders inside /home, which could explain the errors you're getting.

---

### Post by dannyboy79 on 2007-03-02
my 2 cents on this. Is it possible that the directory /tmp/V_FOR_VENDETTA/
isn't there and that's why he's getting this error at the end?
/tmp/V_FOR_VENDETTA/mkisodebug.txt failed!
Also, the permissions issue is another of course as well as the amount of space he has in the folder he is creating his iso file. Also, I noticed when he first was trying to burn to disc, he had the speed set to 8, I would try something lower, like even 2x. that's what I burn at in linux, and I have NO coasters. It's better to take longer than make some coasters!

---

