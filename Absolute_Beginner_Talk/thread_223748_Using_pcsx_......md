---
title: "Using pcsx ....."
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by drosophyllum on 2006-07-26
Im trying to install pcsx but there is an error when running pcsx

"/usr/games/pcsx: line 31: lndir: command not found"

what can I do to fix this? if not possible than does anyone know a ps emulator in a deb package.

Also its been driving me crazy... I cant get visual gamboy adv. emulator to work so does anyone know one that works for them?

here is what I get when I run the EXTREMELY " VISUAL " :D 
emulator

drosophyllum@drosophyllum:/home$ VisualBoyAdvance
VisualBoyAdvance version 1.7.2 [SDL]
Searching for file VisualBoyAdvance.cfg
Searching current directory: /home
Searching home directory: /home/drosophyllum/.vba
Searching system config directory: /etc
Reading configuration file.
Missing image name
VisualBoyAdvance [option ...] file

Options:
  -1, --video-1x               1x
  -2, --video-2x               2x
  -3, --video-3x               3x
  -4, --video-4x               4x
  -F, --fullscreen             Full screen
  -G, --gdb=PROTOCOL           GNU Remote Stub mode:
                                tcp      - use TCP at port 55555
                                tcp:PORT - use TCP at port PORT
                                pipe     - use pipe transport
  -N, --no-debug               Don't parse debug information
  -S, --flash-size=SIZE        Set the Flash size
      --flash-64k               0 -  64K Flash
      --flash-128k              1 - 128K Flash
  -T, --throttle=THROTTLE      Set the desired throttle (5...1000)
  -Y, --yuv=TYPE               Use YUV overlay for drawing:
                                0 - YV12
                                1 - UYVY
                                2 - YVYU
                                3 - YUY2
                                4 - IYUV
  -b, --bios=BIOS              Use given bios file
  -c, --config=FILE            Read the given configuration file
  -d, --debug                  Enter debugger
  -f, --filter=FILTER          Select filter:
      --filter-normal            0 - normal mode
      --filter-tv-mode           1 - TV Mode
      --filter-2xsai             2 - 2xSaI
      --filter-super-2xsai       3 - Super 2xSaI
      --filter-super-eagle       4 - Super Eagle
      --filter-pixelate          5 - Pixelate
      --filter-motion-blur       6 - Motion Blur
      --filter-advmame           7 - AdvanceMAME Scale2x
      --filter-simple2x          8 - Simple2x
      --filter-bilinear          9 - Bilinear
      --filter-bilinear+        10 - Bilinear Plus
      --filter-scanlines        11 - Scanlines
      --filter-hq2x             12 - hq2x
      --filter-lq2x             13 - lq2x
  -h, --help                   Print this help
  -i, --ips=PATCH              Apply given IPS patch
  -p, --profile=[HERTZ]        Enable profiling
  -s, --frameskip=FRAMESKIP    Set frame skip (0...9)
  -t, --save-type=TYPE         Set the available save type
      --save-auto               0 - Automatic (EEPROM, SRAM, FLASH)
      --save-eeprom             1 - EEPROM
      --save-sram               2 - SRAM
      --save-flash              3 - FLASH
      --save-sensor             4 - EEPROM+Sensor
      --save-none               5 - NONE
  -v, --verbose=VERBOSE        Set verbose logging (trace.log)
                                  1 - SWI
                                  2 - Unaligned memory access
                                  4 - Illegal memory write
                                  8 - Illegal memory read
                                 16 - DMA 0
                                 32 - DMA 1
                                 64 - DMA 2
                                128 - DMA 3
                                256 - Undefined instruction
                                512 - AGBPrint messages

Long options only:
      --agb-print              Enable AGBPrint support
      --auto-frameskip         Enable auto frameskipping
      --ifb-none               No interframe blending
      --ifb-motion-blur        Interframe motion blur
      --ifb-smart              Smart interframe blending
      --no-agb-print           Disable AGBPrint support
      --no-auto-frameskip      Disable auto frameskipping
      --no-ips                 Do not apply IPS patch
      --no-mmx                 Disable MMX support
      --no-pause-when-inactive Don't pause when inactive
      --no-rtc                 Disable RTC support
      --no-show-speed          Don't show emulation speed
      --no-throttle            Disable thrrotle
      --pause-when-inactive    Pause when inactive
      --rtc                    Enable RTC support
      --show-speed-normal      Show emulation speed
      --show-speed-detailed    Show detailed speed data
drosophyllum@drosophyllum:/home$


thanks btw drosophyllum is a plant genus that creates sticky globules of acid that smells like honey. It traps insects by the smell then digests it. google it for more info...

---

### Post by bluevoodoo1 on 2006-07-26
> **drosophyllum said:**
> Im trying to install pcsx but there is an error when running pcsx

"/usr/games/pcsx: line 31: lndir: command not found"

what can I do to fix this? if not possible than does anyone know a ps emulator in a deb package.

The epsxe PS emulator works perfectly for me. There's a guide here that works incredibly well for it.



> 
Also its been driving me crazy... I cant get visual gamboy adv. emulator to work so does anyone know one that works for them?

here is what I get when I run the EXTREMELY " VISUAL " :D 
emulator

drosophyllum@drosophyllum:/home$ VisualBoyAdvance
VisualBoyAdvance version 1.7.2 [SDL]
Searching for file VisualBoyAdvance.cfg
Searching current directory: /home
Searching home directory: /home/drosophyllum/.vba
Searching system config directory: /etc
Reading configuration file.
**Missing image name**
[COLOR="Red"]VisualBoyAdvance [option ...] file [/COLOR]

I've never used VisualBoyAdvance, but the output is telling you that you need a file (game) to run (I've put that part in bold). And you have to use it in the context decribed (in red). So if you have a game you should try the terminal command as:

```
VisualBoyAdvance /path/to/game
```

---

