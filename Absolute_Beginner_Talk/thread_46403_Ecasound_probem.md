---
title: "Ecasound probem"
date: 2005-07-04
forum: Absolute Beginner Talk
---

### Post by Buran on 2005-07-04
After installing Ecasound under Synaptic, it didn`t add itsef to the application menu, taping "ecasoun" in Terminal , didn`t make any changes.
How can i start this application ?
 I`ll apriciate any help. ](*,)

---

### Post by poofyhairguy on 2005-07-04
[QUOTE=Buran]After installing Ecasound under Synaptic, it didn`t add itsef to the application menu, taping "ecasoun" in Terminal , didn`t make any changes.
How can i start this application ?
 I`ll apriciate any help. ](*,)[/QUOTE]


try ecasound in terminal. Add the d.

---

### Post by Buran on 2005-07-04
> buran76@ubuntu:~$ ecasound -d
****************************************************************************
*               ecasound v2.3.5 (C) 1997-2004 Kai Vehmanen
****************************************************************************
- [ Session created ] ------------------------------------------------------
(eca-session) Set debug level to: 279
- [ Chainsetup created (cmdline) ] -----------------------------------------
(eca-chainsetup-parser) Set active format to (bits/channels/srate/interleave): s16_le/2/44100/i
(eca-chainsetup) sample rate change, chainsetup command-line-setup to rate 44100.
(eca-chainsetup) Chain "default" created.
(eca-session) Note! Unable to create a valid chainsetup from the command-line arguments.
Warning: DBC_REQUIRE failed - "is_valid()", eca-control-objects.cpp, 455.
Warning: DBC_REQUIRE failed - "selected_chainsetup_repp->is_valid()", eca-session.cpp, 336.
- [ Connecting chainsetup ] ------------------------------------------------
(eca-chainsetup) 'nonrt' buffering mode selected.
- [ Chainsetup connected ] -------------------------------------------------
(eca-controller) Connected chainsetup:  "command-line-setup".
(eca-control) ERROR:  Connecting chainsetup failed: ""
(eca-chainsetup) Deleting chain "default".

That is the terminal recall that i get...

---

