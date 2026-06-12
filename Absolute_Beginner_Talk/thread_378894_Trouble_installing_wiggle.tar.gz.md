---
title: "Trouble installing wiggle.tar.gz"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by dberg on 2007-03-07
I am having trouble installing a program called Wiggle. It is a sound card app for morse code. I have searched in synaptic and could not find the program.

This is what I have done:

```

tar -xvzf wiggle.tar.gz
cd wiggle
./configure
make
sudo checkinstall

```

The ./configure command returns this:

```
bash: ./configure: No such file or directory
```

checkinstall returns this error:

```
make: *** No rule to make target `install'.  Stop.
```

It is then aborted.

Any suggestions?

Thanks.

---

### Post by taurus on 2007-03-07
What's the output of this command while in the wiggle directory?

```
ls -la
```

---

### Post by aysiu on 2007-03-07
You have to [enable extra repositories](http://monkeyblog.org/ubuntu/installing/#enabling_extra_repositories) before you can see it in Synaptic.

[As you can see from the Ubuntu Packages website, *wiggle* is in the Universe repositories](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=wiggle&searchon=name&subword=1&version=all&release=all).

---

### Post by dberg on 2007-03-07
here it is:

```

total 64
drwx------ 3 dberg dberg 4096 2007-03-07 20:04 .
drwxr-xr-x 3 dberg dberg 4096 2007-03-07 19:59 ..
-rwxr-xr-x 1 dberg dberg 7290 2007-03-07 20:01 audiotap
-rw------- 1 dberg dberg  708 2005-10-16 02:42 audiotap.c
-rw-r--r-- 1 root  root    33 2007-03-07 20:04 description-pak
drwxr-xr-x 2 root  root  4096 2007-03-07 20:03 doc-pak
-rwxr-xr-x 1 dberg dberg 7374 2007-03-07 20:01 filter
-rw------- 1 dberg dberg  502 2005-10-16 02:45 filter.c
-rw------- 1 dberg dberg  373 2005-10-16 02:46 Makefile
-rw------- 1 dberg dberg 1153 2005-10-16 02:30 README
-rwxr-xr-x 1 dberg dberg 9287 2007-03-07 20:01 wiggle
-rw------- 1 dberg dberg 3430 2005-10-16 02:26 wiggle.c

```

---

### Post by taurus on 2007-03-07
I bet you can just run it without building anything.

```
./wiggle
```

---

### Post by dberg on 2007-03-07
> **aysiu said:**
> You have to [enable extra repositories](http://monkeyblog.org/ubuntu/installing/#enabling_extra_repositories) before you can see it in Synaptic.

[As you can see from the Ubuntu Packages website, *wiggle* is in the Universe repositories](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=wiggle&searchon=name&subword=1&version=all&release=all).

i saw a program in there called wiggle but it was not the right one, not sure if this is the same one you are talking about or not

---

### Post by dberg on 2007-03-07
> **taurus said:**
> I bet you can just run it without building anything.

```
./wiggle
```

This didn't appear to do anything...

---

### Post by aysiu on 2007-03-07
> **dberg said:**
> i saw a program in there called wiggle but it was not the right one, not sure if this is the same one you are talking about or not
So you're not looking for *a program for applying patches with conflicting changes*? Shucks. Hoped this one could be easy...

---

### Post by dberg on 2007-03-07
> **aysiu said:**
> So you're not looking for *a program for applying patches with conflicting changes*? Shucks. Hoped this one could be easy...

sorry no, it is a program for decoding morse code input through the sound card

---

### Post by taurus on 2007-03-07
What does the README say?

```
more README
```
Hit Space bar for the next 24 lines.

---

### Post by aysiu on 2007-03-07
That's weird. All the files inside the .tar.gz appear to be ASCII.

audiotap.c ```
#include <sys/soundcard.h>
#include <sys/ioctl.h>
#include <fcntl.h>		/* open() */
#include <unistd.h>		/* read(), write() */

int audio_speed = 48000, audio_channels = 1, audio_stereo = 0,
  audio_fmt = AFMT_S16_NE, audio_samplesize = 16;
char *audiodev = "/dev/dsp";

int main (void)
{
  int a;
#define BUFFSIZ 256
  char buffer[BUFFSIZ];

  a = open (audiodev, O_RDONLY, 0);
  ioctl(a, SNDCTL_DSP_CHANNELS, &audio_channels);
  ioctl(a, SNDCTL_DSP_SPEED, &audio_speed);
  ioctl(a, SNDCTL_DSP_STEREO, &audio_stereo);
  ioctl(a, SNDCTL_DSP_SETFMT, &audio_fmt);
  ioctl(a, SNDCTL_DSP_SAMPLESIZE, &audio_samplesize);

  for(;;)
    {
      read (a, buffer, BUFFSIZ);
      write (1, buffer, BUFFSIZ);
    }
}
``` filter.c ```
#include <unistd.h>		/* read() */
#include <math.h>		/* sin() */
#include <stdio.h>
#include <stdlib.h>		/* exit() */

#define SAMP 48000
#define STEP ((2*M_PI*916)/SAMP)

int main (void)
{
  int c=0, d;
  float phase=0;

  for(;;)
    {
      c = 0;
      if (read (0, &c, 2) == 0)
	{
	  fprintf (stderr, "<input exhausted>\n");
	  exit(1);
	}
      if (c > 32768) c = c - 65536;
      d = c * sin (phase);
      phase = phase + STEP;
      if (d < 0) d = 65536 + d;
      write (1, &d, 2);

    }

}
``` Makefile ```
CFLAGS = -O3 -Wall
LDFLAGS =            # for Linux
#LDFLAGS=-lossaudio # for NetBSD

all:	wiggle audiotap filter

wiggle:	wiggle.c
	$(CC) $(CFLAGS) $(LDFLAGS) wiggle.c -o wiggle

audiotap: audiotap.c
	$(CC) $(CFLAGS) $(LDFLAGS) audiotap.c -o audiotap
filter:	filter.c
	$(CC) $(CFLAGS) $(LDFLAGS) filter.c -o filter -lm

clean:
	rm -f wiggle audiotap  *.o *.core *~ filter
``` README ```
Typical usage:

$ audiotap | wiggle 2>/dev/ttyp4

(where "/dev/ttyp4" is another terminal's pseudo-tty, or /dev/null if
you're not interested.)

Note that the audio stream these program munch on is 16 bit signed ints,
in the compiling machine's native endian format.

The "filter" program was a quick experiment to see how well a dumb
idea would work.. (Unfortunately I never got the chance to study
filtering formally, a la` Fourier, FIR, et.al., at Uni during the 10
years I was there.. my B.Sc and B.Math subjects always skirted around
the meaty details.) It was written because sox wouldn't play nice with
pipes. Use it thusly:

$ audiotap | filter | wiggle >/dev/null

(If anyone can get sox's bandpass filters to work in a pipe, please
let me know!)

The trick that wiggle uses to deduce the morse ditrate is to watch for
a dah of carrier, followed by a dit of rest. The combination is 4-dits
in length, and isn't that confusable with another sequence at a
different rate like a dit:on-dit:off or dah:on-dah:off would be.

A big thanks to the operators of my friendly neighbour morse beacon VK2RAG.

-- 
Chris Baird,, <cjb@brushtail.apana.org.au>

``` wiggle.c ```
/* wiggle - morse decoder from soundcard input.
 * --
 * Copyright 2005 Chris Baird <cjb@brushtail.apana.org.au>
 * Licenced according to the GPL V2.
 * --
 * gcc -o wiggle wiggle.c
 * --
 * TODO:
 * command line args:
 * -w nnn: word-wrap after the nnnth column
 * -w nnn: expected wpm?
 * -m    : measure mode; print run timings, etc., instead of letters.
 */

#include <stdio.h>		/* EOF, etc. */
#include <unistd.h>		/* read() */
#include <string.h>		/* strcmp() */
#include <stdlib.h>		/* exit(), calloc() */

#define SAMP 48000
#define SUBSAMP 6
#define EST_WPM (10.0)

char *morse[] =
  {
    "A", ".-",  "B", "-...", "C", "-.-.", "D", "-..",  "E", ".", "F", "..-.",
    "G", "--.", "H", "....", "I", "..",   "J", ".---", "K", "-.-", "L", ".-..",
    "M", "--",  "N", "-.",   "O", "---",  "P", ".--.", "Q", "--.-", "R", ".-.",
    "S", "...", "T", "-",    "U", "..-",  "V", "...-", "W", ".--", "X", "-..-",
    "Y", "-.--","Z", "--..",
    "0", "-----", "1", ".----", "2", "..---", "3", "...--", "4", "....-",
    "5", ".....", "6", "-....", "7", "--...", "8", "---..", "9", "----.",
    ".", ".-.-.-",  ",", "--..--", "?", "..--..", "(", "-.--.",
    ")", "-.--.-",  ":", "---...", "/", "-..-.",  "'", ".----.",
    "\"", ".-..-.", "-", "-....-", "+", ".-.-.",  "=", "-...-",
    "?", "?"
  };

int get_sample (void)
{
  int c = 0;
  if (read (0, &c, 2) == 0)	/* XXX -- obvious endian issue */
    {
      fprintf (stderr, "<input exhausted>\n");
      exit(1);
    }
  /* this gives rectified rather than the usual signed values */
  if (c > 32767) c = 65536 - c;
  return c;
}

int main (void)
{
  int i, d, bp=0, bit, lbit=0, run=1, pass=0, nsamp, ditlength, range;
  int *subsamp, s, tt=0, thres, run1=1;
  char line[80], *lp;

  lp = line;
  /* gives a rough number of measurements needed to make SUBSAMP samples
   * per dit. apparently there's 5/12 dits per second at 1 WPM */
  nsamp = (SAMP*5) / (EST_WPM*12*SUBSAMP);
  ditlength = SUBSAMP;

  range = (8*12*EST_WPM*SUBSAMP) / 5; /* 8 seconds' worth */
  subsamp = (int*)calloc (range, sizeof(int));

  /* main decoding loop */
  for (;;)
    {
      for (s = 0, i=0; i < nsamp; i++)
	s += get_sample();

      tt = tt + s - subsamp[bp];
      subsamp[bp] = s;
      bp = (bp+1) % range;

      /* wait until we have an idea of the average signal level */
      if (++pass < range)
	{
	  fprintf (stderr, "%d \r", range-pass);
	  continue;
	}

      thres = tt / range;
      bit = (10*s) > (12*thres) ? 1 : 0;

      if (bit == lbit)
	{
	  run++;
	  continue;
	}

      d = (10*run) / ditlength;

      if (lbit == 1)
	{
	  if ((d > 5) && (d < 20))
	    *lp++ = '.';
	  if ((d >= 20) && (d < 40))
	    *lp++ = '-';
	  *lp = '\0';
	  run1 = run;
	  if (lp == &line[79]) lp--; /* prevent overflow */
	}

      if ((lbit == 0) && (lp != line))
	{
	  if (d >= 20)
	    {
	      for (i=0; *morse[i+1] != '?'; i += 2)
		if (strcmp (morse[i+1], line) == 0)
		  break;
	      if (*morse[i+1] == '?')
		printf ("%s", line);
	      else
		printf ("%s", morse[i]);
	      if (d > 80)
		printf (" ");
	      fflush (stdout);
	      lp = line;
	    }
	  /* check if a "dah-do" */
	  if ((run1 > 2) && ((run1) > (2*run)))
	    {
	      d = (run+run1) / 4;
	      if ((d > (SUBSAMP/2)) &&
		  ((3*d) > (2*ditlength)) && ((2*d) < (3*ditlength)))
		{
		  ditlength = d;
		  fprintf (stderr, "<%d>",ditlength);
		}
	      run1=0;
	    }
	}
      lbit = bit;
      run = 1;
    }
}
``` Does the *.c* extension mean it's written in C and needs to be compiled?

---

### Post by dberg on 2007-03-07
was that a question to me, cause if it was I have no idea...

---

### Post by aysiu on 2007-03-07
> **dberg said:**
> was that a question to me, cause if it was I have no idea...
Actually, it was to taurus or anyone else reading.

I know nothing about compiling stuff...

---

### Post by dberg on 2007-03-07
if anyone would like to see the files to try it they are here:

[http://radio.linux.org.au/pkgdetail.phtml?sectpat=morse&ordpat=title&descpat=&pkgid=419]("http://radio.linux.org.au/pkgdetail.phtml?sectpat=morse&ordpat=title&descpat=&pkgid=419")

---

### Post by aysiu on 2007-03-07
> **dberg said:**
> if anyone would like to see the files to try it they are here:

[http://radio.linux.org.au/pkgdetail.phtml?sectpat=morse&ordpat=title&descpat=&pkgid=419]("http://radio.linux.org.au/pkgdetail.phtml?sectpat=morse&ordpat=title&descpat=&pkgid=419")
I also posted their contents in post #11.

---

