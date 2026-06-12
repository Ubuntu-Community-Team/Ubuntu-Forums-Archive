---
title: "Environment variables not working properly"
date: 2011-12-19
forum: Any Other OS
---

### Post by ChimeraMica on 2011-12-19
I recently purchased the Humble Indie Bundle #4 and during the process of getting this set up, I came across some issues. It turns out the binary required a different version of g++, and I was able to find the proper library in another game's directory. To make a long story short, I made a .desktop at  /usr/share/applications/bit-trip-runner.desktop with the following contents:

```
[Desktop Entry]
Version=1.0
Type=Application
Name=Bit.Trip Runner
Comment=A retro-styled musical platformer
Exec=LD_LIBRARY_PATH=/home/mica/.bit-trip-runner/depends /usr/bin/bit.trip.runner
Icon=/usr/share/icons/hicolor/192x192/apps/bit-trip-runner.png
Categories=Game
```This worked well enough, but I decided that since some other games were also missing the right dependencies, and some were shared, I'd make a global location for the missing libraries.

```
Exec=LD_LIBRARY_PATH=/opt/humble-bundle/ /usr/bin/bit.trip.runner
```This didn't work. I also tried launching it from the terminal (minus the "Exec=") and that worked. Needless to say I'd like to get things working. The original .desktop configuration would still work, but I'm striving for elegance and I'm also struck with a great deal of curiosity. I'm running 64-bit Linux Mint 11 "Katya" Thank you in advance.

---

### Post by fdrake on 2011-12-19
you have to export the variable to make it available to the shells child process (if i understood clearly your question..)
```

export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/opt/humble-bundle/:/usr/bin/bit.trip.runner

```

to make it global do:
```

echo "LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/opt/humble-bundle/:/usr/bin/bit.trip.runner" >> ~/.bashrc

```

---

### Post by Perfect Storm on 2011-12-19
Moved to Other OS/Distro Talk.

---

### Post by ChimeraMica on 2011-12-19
Hmm, the former worked, but when I try to set it globally I get this:

```
# "LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/opt/humble-bundle/:/usr/bin/bit.trip.runner" >> ~/.bashrc
bash: LD_LIBRARY_PATH=:/opt/humble-bundle/:/usr/bin/bit.trip.runner: No such file or directory
```The strange thing is that when I set the variable to the folder in my home directory, it works fine.

Oh, and it also works when I type it into the terminal emulator.

---

### Post by Interruptor on 2012-02-19
Use
```
Exec=env LD_LIBRARY_PATH=/opt/humble-bundle/ /usr/bin/bit.trip.runner
```

---

