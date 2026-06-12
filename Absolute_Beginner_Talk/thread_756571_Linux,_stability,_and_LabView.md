---
title: "Linux, stability, and LabView"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by jaredssix on 2008-04-16
Hey all,

I am designing a control system and dosing mechanism for testing onsite wastewater treatment units at an outdoor facility on campus. I will be using LabView to run the dosing mechanism and check the system for failures. 

The testing regime spans six months per wastewater treatment unit, and we will have up to five units being dosed at any given time. For obvious reasons, stability is a great consideration.

I have heard many times the stability of Linux touted. Would you of the forums recommend controlling this wastewater treatment testing facility running Labiew through  a Linux system vs another OS? 

(Do I already know the answer to this question?)

---

### Post by Whiffle on 2008-04-16
Honestly, if the only thing the computer is doing is LabView, windows or linux probably won't be much of an issue.  However, I do feel that linux is generally more stable and reliable assuming your'e not constantly updating it (which is where I usually run into issues).

---

### Post by Ozitraveller on 2008-04-16
I got this from their website, looks like it runs on linux already.


 LabVIEW 8 for Linux, the latest version of the LabVIEW graphical development platform, includes numerous new features for test and control applications. These features include:

    * Project-based development for large applications
    * Simplified distributed communication with the shared variable
    * Instrument Driver Finder for locating and installing instrument drivers
    * Instrument Driver Project Wizard for developing instrument drivers
    * Project library for restricted code reuse
    * Redesigned Application Builder
    * 150 new and enhanced analysis VIs
    * Structures for disabling code during compilation and execution
    * Splitter bars for creating professional user interfaces
    * XY graph planes (Nyquist, Nichols, Z Plot, S Plot)
    * Simplified VI Server programming with LabVIEW Class Browser
    * Mixed-signal graph for displaying both analog and digital data
    * Custom run-time shortcut menus for front-panel controls and indicators
    * Additional front-panel object events including data drag and drop

LabVIEW includes hundreds of built-in functions designed specifically for extracting useful information from acquired data and for analyzing measurements and processing signals.

LabVIEW also provides tools for user interface design, data presentation, communication via TCP/IP, Web publishing, report generation, data management, and integrating external code.

---

### Post by The Cog on 2008-04-16
Whiffle is probably right - if you just install one application and leave it alone, both OSs will probably prove stable. I would personally have the following concerns about using Windows though:

1) Windows is generally regarded as needing regular updates. It may possibly be (I don't know) that windows cannot run for more than a few weeks without reboot.

2) Windows AV software, likewise, needs regular updates, although I don't think this normally involves a reboot.

3) XP and previous versions are obsolete. But would you trust Vista to keep running reliably for that long?

I may be doing windows a disservice, but I would personally feel much happier about leaving a Linux box running and coming back 6 months later than I would a Windows box. You can probably significantly improve the chances of success with Linux if you kill the GUI and leave it in a tty console when you leave it.

P.S.
<rhetorical>What kind of answer did you expect from a Linux users forum?</rhetorical>

P.P.S.
You might be better off with Debian Stable than with Ubuntu for stablilty. Solaris might also be worth considering.

---

### Post by jaredssix on 2008-04-16
Thanks for the insight, gang! 

Yeah, that's more or less what I expected to hear from you lot, and what I wanted to hear. 
I'll run it by the LabView wizards, the IT/Linux/everything else wizards, and my advisors and see what we settle on. 

--Jared

---

