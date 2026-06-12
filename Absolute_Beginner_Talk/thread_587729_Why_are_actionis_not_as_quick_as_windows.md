---
title: "Why are actionis not as quick as windows?"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by XNYE on 2007-10-23
On my desktop I'm using WinXP Pro and ubuntu on a notebook.  An example of what I mean is, Firefox... on my desktop going from tab to tab is very instantaneous.  On my notebook it's slower.. maybe I just haven't set something correctly?  

Is it because I'm using restricted drivers?? (I'm assuming restricted drivers are drivers that aren't recommended but I can use them to make my workstation work properly)


Desktop:
P4 3.0ghz 1gb x300 7200rpm
Notebook:
C2D 1.6ghz 1gb 8400gs 5400rpm

Is it because of the slower HDD? or is my proc not good enough?  I know the GPU is not the best.

Thanks.

---

### Post by Shazaam on 2007-10-23
Desktop= faster processor and hard drive.

---

### Post by Pinger05 on 2007-10-23
Did you have XP on the laptop prior to the Ubuntu installation?  If so did you "time" how long it took you to do things?

The reason I bring this up is it seems to me that the laptop is much slower than the desktop and as such there may be some precieved 'hesitation' on the laptop.

If the hesitation is causing you to re-think the decision of Ubuntu try installing XP on a virtual machine in Ubuntu.  This will tell you if it is truly the laptop or if it is Ubuntu.

---

### Post by georghess on 2007-10-23
> **XNYE said:**
> On my desktop I'm using WinXP Pro and ubuntu on a notebook.  An example of what I mean is, Firefox... on my desktop going from tab to tab is very instantaneous.  On my notebook it's slower.. maybe I just haven't set something correctly?  
.

I have been running WinXP and Ubuntu on two identical laptops side by side and found NO difference in firefox and OpenOffice program performance ... (not a serious tedt) :-)

---

### Post by XNYE on 2007-10-23
Thanks guys.... not a huge buff on hardware speeds and such. I did have WinXP Home installed.. I did have firefox on it but can't remember being distracted by the speed of things.

I assumed since this was newer hardware (2007) than my desktop (2005) that the low end laptop might match the older desktop... I didn't realize that a P4 3.0 is still good these days?

I thought I had read some where that a 1.6ghz notebook was equivalent to a 3.0ghz desktop cpu.

I really am quit use to the faster cpu.  I guess I should have looked into hardware more before ordering but people said that 1.6ghz would be fine for a notebook.   Maybe I should return the laptop and opt for a 2.0ghz CPU.  I would do that before quiting on ubuntu at this point.   I didn't think that 1.6ghz would be so slow. (when I say slow I mean to what I'm use to.  I mean it's not slow but it is for me. If that makes any sense)  

I didn't know the HDD really made that much of a difference with web browsers.

---

### Post by vertexoflife on 2007-10-23
Are you running 7.10, Gutsy Gibbon?

I found firefox to be incredibly slow in Gutsy Gibbon, but I found by reading somewhere that this could be something called IPV6. When I disabled IPV6, firefox ran much, much faster.

Try this: 

1. Open up a new firefox tab, type about:config in the address bar.

2. Scroll down down down until you get to " network.dns.disableIPv6 " It says false by default. Set it to true by double clicking on it.

3. Restart firefox.

4. Report Back to us. =)

---

### Post by XNYE on 2007-10-23
it seems slightly faster than before.. not up to par with my desktop.  Um... also I'm seeing this marqueeing icon that looks like a piece of paper if I switch tabs quickly... sort of annoying.

---

### Post by MatthewPlanchard on 2007-10-23
or you could try [swiftfox]("http://getswiftfox.com/")
it simply is just a swifter fox

---

### Post by XNYE on 2007-10-23
Oh, and yes I'm using Ubuntu 7.10

hmm, I guess I could use that substitution if I must.

---

### Post by vertexoflife on 2007-10-23
You know, it could be the fact that Compiz is really just slowing your system down.

Try installing compizconfig-settings-manager

( sudo apt-get install compizconfig-settings-manager ) Tweak with it a bit and see if you can cut down on slowness that way.

---

### Post by Dapman01 on 2007-10-23
Just as an fyi a 1.8 ghz core 2 duo will kill a 3.0 ghz p4
They run on different architecture, the p4 was designed to give those huge clock speed numbers with the netburst archetecture, but in reality they were slow and ran very, very hot.

The quicker hard drive will only matter on loading speeds, and even those aren't that much

---

### Post by XNYE on 2007-10-23
> **vertexoflife said:**
> You know, it could be the fact that Compiz is really just slowing your system down.

Try installing compizconfig-settings-manager

( sudo apt-get install compizconfig-settings-manager ) Tweak with it a bit and see if you can cut down on slowness that way.

Really?! :(  I thought linux was awsome for low end computers... I know my notebook isn't the greatest but it isn't the lowest of the low ):

So you're saying I need a new notebook? ):  I guess I'm willing to spend 150-200 more bucks for ubuntu but I thought the point was to save on hardware costs for this OS.  Maybe I can sell some of my 360 games and my watch to upgrade notebooks :(

---

### Post by jusmurph on 2007-10-23
> **XNYE said:**
> 
Desktop:
P4 3.0ghz
Notebook:
C2D 1.6ghz
[

CPU is twice as fast...

That does not mean the computer is necessarily twice as fast but umm... perhaps try comparing apples with apples :confused:

---

### Post by XNYE on 2007-10-23
> **Dapman01 said:**
> Just as an fyi a 1.8 ghz core 2 duo will kill a 3.0 ghz p4
They run on different architecture, the p4 was designed to give those huge clock speed numbers with the netburst archetecture, but in reality they were slow and ran very, very hot.

The quicker hard drive will only matter on loading speeds, and even those aren't that much

Yeah, I thought the HDD wouldn't help much.  "Loading speeds" that's what I was thinking about but couldn't think of it haha.

I was reading when I was deciding on CPUs that the 1.6 wasn't much of a difference to a 1.8.

I do love my P4 though... it's fast... at least I think it's fast.  (I want to "know" faster!)

---

### Post by bobplano on 2007-10-23
compiz-fusion is included by default in gutsy. it is kind've resource intensive, especially on a laptop which sometimes doesn't have dedicated memory for graphics. you could try turning the effects off temporarily and see what the difference in speed is

---

### Post by XNYE on 2007-10-23
> **bobplano said:**
> compiz-fusion is included by default in gutsy. it is kind've resource intensive, especially on a laptop which sometimes doesn't have dedicated memory for graphics. you could try turning the effects off temporarily and see what the difference in speed is

Turn effects off?! NEveR!

I will though.

---

### Post by XNYE on 2007-10-23
> **XNYE said:**
> Turn effects off?! NEveR!

I will though.

noooo... it did speed things up. ): my notebook suckss. I hate you notebook. I guess this means I need more RAM.

EDIT: I noticed that I had my workspace transparent from the >Desktop Cube settings>Transparency whilst not rotating.  I must have forgotten I had done so in the midst of my ubuntu excitement.  (I'm new! I don't know what to do!)
That helped... :-/ But I want that enabled!

Should I mark this as solved?

---

### Post by Dapman01 on 2007-10-25
> **XNYE said:**
> Yeah, I thought the HDD wouldn't help much.  "Loading speeds" that's what I was thinking about but couldn't think of it haha.

I was reading when I was deciding on CPUs that the 1.6 wasn't much of a difference to a 1.8.

I do love my P4 though... it's fast... at least I think it's fast.  (I want to "know" faster!)

I'm typing on a computer that has a 4000+ AMD in it, it would take a pentium 4 faster than 4Ghz to keep up with it, and that is before overclocking

In my gaming machine I have a 3800+ x2 running @ 5800+ status

---

### Post by mmmfottrell on 2007-10-25
[www.puppylinux.org](www.puppylinux.org)





:popcorn:

---

### Post by XNYE on 2007-10-25
> **Dapman01 said:**
> I'm typing on a computer that has a 4000+ AMD in it, it would take a pentium 4 faster than 4Ghz to keep up with it, and that is before overclocking

In my gaming machine I have a 3800+ x2 running @ 5800+ status

AMD is foreign to me.. 4000, 3800 have no meanings to me.   For some reason I've always stuck with Intel.. I'm guessing 4000+ is expensive? In which, I don't want to know fast then. :)  I want to know fast at a reasonable price :)

puppylinux comes with compiz?  Okay.. puppylinux is for old computers? Mine isn't old >:O

---

