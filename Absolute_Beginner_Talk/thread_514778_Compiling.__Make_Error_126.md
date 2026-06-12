---
title: "Compiling.  Make Error 126"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by joeldi on 2007-08-01
I've been trying to compile and install ZSNES from source.  It's the first time I've tried to compile from source.  I'm on Dapper.

After doing everything that pretty much all the help sites I could find told me, I'm still met with

/bin/sh: tools/depbuild: cannot execute binary file
make: *** [makefile.dep] Error 126

Which shows up after about 10 lines of gibberish, which I assume is part of the normal compiling process.

Googling that exact error was no help, I hope I can find help here.
Thanks.

---

### Post by Regel on 2007-08-01
I suggest you use 'checkinstall' instead of make because checkinstall creates .deb-files so it's easier to uninstall them.

But to the problem.
Are all the depencies met?

---

### Post by joeldi on 2007-08-02
I'm sure I'm not getting any message that explicitly tells me that I don't have all the required packages.  I'll post the output from the entire process.

And I decided I'd try it with checkinstall, and got the exact same error message.


```

========================= Installation results ===========================
tools/depbuild gcc " -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include/SDL -D_REENTRANT  -D__OPENGL__ -march=k8 -O3 -fomit-frame-pointer -s" nasm " -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1" cfg.o endmem.o init.o initc.o input.o md.o patch.o ui.o vcache.o version.o zloader.o zmovie.o zpath.o zstate.o ztime.o ztimec.o chips/c4emu.o chips/c4proc.o chips/dsp1emu.o chips/dsp1proc.o chips/dsp2proc.o chips/dsp3emu.o chips/dsp3proc.o chips/dsp4emu.o chips/dsp4proc.o chips/fxemu2.o chips/fxemu2b.o chips/fxemu2c.o chips/fxtable.o chips/obc1emu.o chips/obc1proc.o chips/sa1proc.o chips/sa1regs.o chips/sdd1emu.o chips/seta10.o chips/sfxproc.o chips/st10proc.o chips/7110proc.o chips/seta11.o chips/st11proc.o cpu/dma.o cpu/dsp.o cpu/dspproc.o cpu/execute.o cpu/executec.o cpu/irq.o cpu/memory.o cpu/memtable.o cpu/spc700.o cpu/stable.o cpu/table.o cpu/tablec.o debugasm.o debugger.o gui/gui.o gui/guifuncs.o gui/menu.o effects/burn.o effects/smoke.o effects/water.o jma/7zlzma.o jma/crc32.o jma/iiostrm.o     jma/inbyte.o jma/jma.o jma/lzma.o       jma/lzmadec.o jma/winout.o jma/zsnesjma.o mmlib/mm.o mmlib/linux.o  video/makev16b.o video/makev16t.o video/makevid.o video/mode716.o video/mode716b.o video/mode716d.o video/mode716e.o video/mode716t.o video/mode7.o video/mode7ext.o video/mv16tms.o video/m716text.o video/newg162.o video/newgfx.o video/newgfx16.o video/newgfx2.o video/procvid.o video/procvidc.o video/sw_draw.o video/2xsaiw.o video/hq2x16.o video/hq2x32.o video/hq3x16.o video/hq3x32.o video/hq4x16.o video/hq4x32.o video/ntsc.o video/copyvwin.o linux/audio.o linux/battery.o linux/sdlintrf.o linux/sdllink.o linux/gl_draw.o linux/sw_draw.o linux/safelib.o zip/unzip.o zip/zpng.o > makefile.dep
/bin/sh: tools/depbuild: cannot execute binary file
make: *** [makefile.dep] Error 126

****  Installation failed. Aborting package creation.
```

---

### Post by joeldi on 2007-08-06
Bump (The rules said bumping was permitted.  Is there something else I should be saying in this post?)

---

