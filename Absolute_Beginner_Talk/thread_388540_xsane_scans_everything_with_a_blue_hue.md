---
title: "xsane scans everything with a blue hue"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by marmaladejackson on 2007-03-19
Hey all,
Just got my scanner working last night.  For black and white it looks great.  With color... almost every scan has a blue hue.  Every 3 or 4 scans, I get a normal picture but everything else is bluish. I've played around with the gamma settings, but i don't think they're the problem, just because if I hit the "scan" button enough, eventually one will pop up normal.  Anybody encounter this before?

-B

---

### Post by OMRebel on 2007-03-19
What scanner are you using? (brand and model)

---

### Post by marmaladejackson on 2007-03-19
Oh yeah.... Visioneer 7300 one touch.
Sorry shoulda put that in the original post.

---

### Post by henriquemaia on 2007-04-06
> **marmaladejackson said:**
> Hey all,
Just got my scanner working last night.  For black and white it looks great.  With color... almost every scan has a blue hue.  Every 3 or 4 scans, I get a normal picture but everything else is bluish. I've played around with the gamma settings, but i don't think they're the problem, just because if I hit the "scan" button enough, eventually one will pop up normal.  Anybody encounter this before?

-B

Hi,

I have a problem similar to yours, even though I'm using a Mustek Bearpaw 1200. Color scanning works fine at first scanning (when you start xsane) but on next scannings everything becomes bluish. I have to restart xsane for every color scan I do. A bug?

specs: Ubuntu 6.10, Mustek Bearpaw 1200, xsane 0.991

---

### Post by abeowitz on 2007-09-08
Same problem here... 

I have the latest CVS and gt68xx backends & frontends compiled from scratch, too.

Anyone know why and if there's a solution?

---

### Post by alienexplorers on 2007-09-08
My Microtek Scanmaker 4800 scanns everything with a yellow hue.  Any way to fix it.

---

### Post by alienexplorers on 2007-09-09
bump

---

### Post by abeowitz on 2007-09-09
OK, here's the deal, as far as I can tell.

I dug into the source code and it has to do with a timing or exposure calibration for each of the red/blue/green.  

Apparently there's a 'test pattern' just under the lip where the scan head parks itself.  This is a known good image and it tests against that to get the right RGB values.  

If you watch, you can see the llights flicker just before the scan starts.  This is the calibration part.

My scanner (Visioneer 7300 One Touch) seems to work by using red/blue/green lights against the image and then using a monochrome light sensor to detect the resulting values.  If you blink or move your eyes while watching the scan, you'll see each of the three colors.  The main color you see is probably the longest running exposure time.

Where it fails is it's not given enough time to find the right red/blue exposure settings.  So, you'll see this error:  **"gt68xx_afe_cis_auto: setting exposure reached limit"**

Now I have no clue how it figures out the right colors & brightness, but if the algorithm can't figure out the right exposure it will simply scan with whatever its got.  

And sometimes it would end up with values that work.

So, I dug into the source code and found part of the algorithm here...

By adding 75 to the 'too low' equation, and 7 to the 'too high', I was able to get my scanner to calibrate much faster.

```
static SANE_Bool
gt68xx_afe_cis_adjust_exposure (SANE_String_Const color_name,
                                GT68xx_Afe_Values * values,
                                unsigned int *white_buffer, SANE_Int border,
                                SANE_Int * exposure_time)
{
  SANE_Int exposure_change = 0;

  gt68xx_afe_cis_calc_white (values, white_buffer);

  if (values->white < border)
    {
      exposure_change = (((border** + 75**) - values->white) * 1);
      (*exposure_time) += exposure_change;
      DBG (4,
           "%5d %5s: white = %3d, total_white=%5d (exposure too low) --> exposure += %d (=0x%03x)\n",
           border, color_name, values->white, values->total_white, exposure_change, *exposure_time);
      return SANE_FALSE;
    }
  else if (values->white > border **+ 7**)
    {
      exposure_change = -((values->white - (border **+ 7**)) * 1);
      (*exposure_time) += exposure_change;
      DBG (4,
           "%5s: white = %3d, total_white=%5d (exposure too high) --> exposure += %d (=0x%03x)\n",
           color_name, values->white, values->total_white, exposure_change, *exposure_time);
      return SANE_FALSE;
    }
  else
    {
      DBG (4, "%5s: white = %3d, total_white=%5d (exposure ok=0x%03x)\n",
           color_name, values->white, values->total_white, *exposure_time);
    }
  return SANE_TRUE;


```

Now, this could be the totally wrong way to do it, but like I said, i don't understand what's going on with 'border', white values, etc.

So, you can make these changes and recompile.  I'd be curious if these values work for other people/scanners.

(Note that --prefix=/usr points the etc/sane.d config files in /usr/etc/sane.d... dunno how to fix that yet.)

**ANOTHER important note.**  You can shorten the delay to scan by 1/2 just by adding the afe debug line output to gt68xxx.conf under your scanner section.  Read the man page for how to do that.  

So, with the afe rough calibration and the exposure code changes above, I was able to get my scanner to consistently scan the right colors, AND almost completely eliminate the delay before the scanner starts moving.  :)

I don't know exactly how that all works, but I'm good for now.  

Good luck!

---

### Post by abeowitz on 2007-09-09
```
scanimage --mode Color --depth 12 --resolution 300 --full-scan > out.pnm
```

Gives me the top calibration lines.  A big white area and a black area.  

[IMG]http://www.spellcheckcomic.com/misc/scanner_calibration.jpg[/IMG]

I expected to see red/blue/green areas, too.  But I guess not.  Hmmm... how does this work?

---

### Post by peterx14 on 2007-09-09
I'm getting a similar problem on my scanner -- a CanoScan FB630U. In my case, scanning white paper gives it a kind of greenish tint; when I load the output into an image editor, I'm getting RGB values like: #DDDCC5 where I'd expect something nearer white.... in fact, checking an older scan that was from the same scanner under Windows, the white paper is mostly #FEFEFE.

---

