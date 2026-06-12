---
title: "Ubuntu MythTV Advice /Recommendations"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by Chewiesw on 2007-01-16
Hiya

I have just started playing around with Linux\ubuntu and getting to grips with it and I thought a nice project would be to build a myth box (standalone). I need some advice /recommendations on what capture card to get, I am stuck as whether to get two pvr 150's or a pvr500 card, I have read in forums that the quality of the pvr 500 can be a bit shoddy.

Something else I am struggling to get my head around also is how you connect the box to your TV, I presume you use our graphic card and some how convert it to scart?


I intend hooking up the box to a dual view sat decorder

I would also appreciate any other advise anyone one can give me from their own experiences

Cheers

---

### Post by wilderness wanderer on 2007-01-17
> **Chewiesw said:**
> Hiya

I am stuck as whether to get two pvr 150's or a pvr500 card, I have read in forums that the quality of the pvr 500 can be a bit shoddy.

I just went with one pvr-150 for now, only $60 for the unit without the remote (I already had a remote).  I can always add another at a later time.  I don't know much about the pvr-500 but it seems like the IVTV driver support for the 150 is more mature.

> Something else I am struggling to get my head around also is how you connect the box to your TV, I presume you use our graphic card and some how convert it to scart?

You'll want to make sure you have a video card which has a TV-out jack (usually S-video and composite) that is supported by Linux.  Then you just run a cable from the tv out to your TV or A/V receiver like you would a DVD player or any other video component.

The other option you may want to look into here (especially if you are considering setting up on an older/slower computer) is using a PVR-350 card, which has a built-in TV out as well as a hardware MPEG-2 decoder.  From what I have read the setup of the tv out on this card can be a little tricky, but people are having success diong it.  With a PVR-350 plus a PVR-150 you would have hardware acceleration of both the encoding and decoding of MPEG-2 video, so you could get by with a much slower CPU.


>  intend hooking up the box to a dual view sat decorder

I assume this means you need to change channels on the satellite box.  Make sure you get a card with the IR blaster included.

Hope this helps.  My setup is very simple-- One tuner card on analog cable.  So I'm afraid I can't be much help to your situation.

---

### Post by adamantivm on 2007-01-17
I've been using the pvr-500MCE for over a year and have absolutelly no complains. My use of this card spans a few different Fedora Distros as well as an Ubuntu Distro now. I also used it under Intel P4 and now with an AMD using the amd64 distro. Never a problem.

---

