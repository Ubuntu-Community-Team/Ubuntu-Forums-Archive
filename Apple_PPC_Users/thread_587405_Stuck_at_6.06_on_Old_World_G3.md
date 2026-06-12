---
title: "Stuck at 6.06 on Old World G3"
date: 2007-10-22
forum: Apple PPC Users
---

### Post by smileyme on 2007-10-22
A couple years ago I installed 5.10 on a heavily upgraded G3 AIO; 83 MHz bus and 450 G3 running at 500 MHz. Due to the difficulty in installing from scratch, I upgraded to 6.06 through the dist-upgrade. I then kind of lost interest in the project until recently when I upgraded my PC to 7.04, and now to 7.10. I again tried to upgrade the AIO, but get no options to upgrade beyond 6.06. Software updater says system is up to date. I tried apt-get, but no joy. What am I doing wrong.

Rick :)

PS: I should have been writing this from the AIO, and will in the future.

---

### Post by Tommy on 2007-10-22
> **smileyme said:**
> A couple years ago I installed 5.10 on a heavily upgraded G3 AIO; 83 MHz bus and 450 G3 running at 500 MHz. Due to the difficulty in installing from scratch, I upgraded to 6.06 through the dist-upgrade. I then kind of lost interest in the project until recently when I upgraded my PC to 7.04, and now to 7.10. I again tried to upgrade the AIO, but get no options to upgrade beyond 6.06. Software updater says system is up to date. I tried apt-get, but no joy. What am I doing wrong.

Hi! Ubuntu quit supporting our Oldworlds long ago, but we MAY be able to get beyond Dapper 6.06.1 with some effort. I have a lot of hope that Gutsy will someday  work with Oldworld, but it's not even working consistently with newworld Macs at the moment -- there are some "show-stopper" bugs such as the one that won't load the hard drive and CD drivers with the kernel.

For the moment I'm sticking with Dapper and will suggest you may want to wait too. When you're ready I recommend NOT attempting an "upgrade." Ubuntu only supports doing an upgrade going from one point release to the next, so you would go from 6.06 to 6.10 to 7.04 to 7.10. That would take A LOT of time and I can guarantee something will break in the process.

Theoretically Ubuntu will support going directly from 6.06 LTS to the next "LTS" (long term support) release. I'm not sure which that will be, but maybe 8.04...? 

I can't vouch for PowerPC, but that might end up being the shortcut we need on our oldworlds.

---

### Post by smileyme on 2007-10-22
> **Tommy said:**
> Hi! Ubuntu quit supporting our Oldworlds long ago, but we MAY be able to get beyond Dapper 6.06.1 with some effort. I have a lot of hope that Gutsy will someday  work with Oldworld, but it's not even working consistently with newworld Macs at the moment -- there are some "show-stopper" bugs such as the one that won't load the hard drive and CD drivers with the kernel.

For the moment I'm sticking with Dapper and will suggest you may want to wait too. When you're ready I recommend NOT attempting an "upgrade." Ubuntu only supports doing an upgrade going from one point release to the next, so you would go from 6.06 to 6.10 to 7.04 to 7.10. That would take A LOT of time and I can guarantee something will break in the process.

Theoretically Ubuntu will support going directly from 6.06 LTS to the next "LTS" (long term support) release. I'm not sure which that will be, but maybe 8.04...? 

I can't vouch for PowerPC, but that might end up being the shortcut we need on our oldworlds.
I had expected to need to upgrade to each release in turn with 6.10 being first, but even that doesn't seem to be an option. So, I guess, for the moment I too am sticking with 6.06, but the AIO is just a novelty anyway.:lolflag:

Rick :)

---

