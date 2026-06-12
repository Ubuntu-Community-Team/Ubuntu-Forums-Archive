---
title: "From ML: Fixing brittle speech support on Dapper"
date: 2006-06-13
forum: Assistive Technology &amp; Accessibility
---

### Post by Henrik on 2006-06-13
I'm re-posting this mailing list post by Enrico Zini in the hope that someone in the forums an help. He is working on making an accessible environment in Italian based on Dapper, so it would be great if he could find a way around this hurdle. 

-------

- speech doesn't work anymore.  test-speech exits with:
>    Exception Unknown CORBA exception id: 'IDL:omg.org/CORBA/COMM_FAILURE:1.0' getting voice list.

I tried reinstalling from scratch in another computer, and I can
trivially reproduce the speech server lockup there as well:

 1) Fresh Ubuntu Dapper, apt-get install festlex-ifd festvox-italp16k
    festvox-itapc16k (from universe)
 2) go to gnopernicus Preferences/Speech/Voices/Modify absolute values
 3) choose "Festival GNOME Speech Driver" as a driver, "V2 lp_diphone"
    as the voice.  Apply setting for all voices.
 4) close the window.  The voice stops.  test-speech hangs after
    selecting the festival server.

Please help me to find some clues on fixing this: it took us years to
get GPL Festival voices for Italian, and now we could easily turn them
into an accessible localised desktop, if it weren't for this.

----------

Original: [https://lists.ubuntu.com/archives/ubuntu-accessibility/2006-June/000518.html](https://lists.ubuntu.com/archives/ubuntu-accessibility/2006-June/000518.html)

---

