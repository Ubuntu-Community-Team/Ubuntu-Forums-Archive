---
title: "My Movie Player Does Not Work"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by ^Usa^DonkeyPunch on 2006-10-05
It will play to an exstent and then it just shuts off........
my freind who works at the local BGC Club aka: Boys and girls club
install kubuntu on my computer and i am a total newbie!!! at useing konsole
please help me and it will be appreciated
Thx:-D

---

### Post by ^Usa^DonkeyPunch on 2006-10-05
Bump

---

### Post by james_san on 2006-10-05
use Synaptic Package Manager to install "mplayer". That is the bulletproof movie player for linux. (You may need to enable all the repositories in Settings -> Repositories and reload the package list before it shows up)

---

### Post by ^Usa^DonkeyPunch on 2006-10-05
alright ill try that 1 sec k?

---

### Post by james_san on 2006-10-05
ok. :)

---

### Post by ^Usa^DonkeyPunch on 2006-10-05
did not work man please try to explain more it says that its not running?

---

### Post by ^Usa^DonkeyPunch on 2006-10-05
i get
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread3/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdread: DVDDiscId read returned -1 bytes, wanted 90112
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread3/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
FATAL[ogle_mpeg_ps]: dvdreadblocks failed
donkeypunch@Lockout:~$ xine
bash: xine: command not found
donkeypunch@Lockout:~$ kmplayer
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kmplayer: View 50331893
kmplayer: ImageRuntime::remoteReady image/gif 8852
kmplayer: ImageRuntime::remoteReady image/png 5558
kmplayer: playingStopped 0x81150c8
kmplayer: PartBase::openURL false
kmplayer: processState Not Running -> Ready

---

### Post by james_san on 2006-10-15
> Many DVDs use css. To play these discs, a special library is needed to decode
them, libdvdcss. Due to legal problems in some particular countries, Debian
cannot distribute libdvdcss.

If it is legal for you to use css in your country, you can:

        * Install the packages from <http://www.debian-unofficial.org/>.

        * Run /usr/share/doc/libdvdread3/install-css.sh
          This script needs wget and will download (a rather outdated) package
          from the upstreams website of libdvdread.

Open up a konsole and type `sudo usr/share/doc/libdvdread3/install-css.sh` (without the quotes), press enter, type your password, enter again. That should fix it :)

---

