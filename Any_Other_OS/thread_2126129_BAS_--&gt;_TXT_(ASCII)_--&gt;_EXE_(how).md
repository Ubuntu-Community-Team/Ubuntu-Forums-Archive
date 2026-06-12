---
title: "BAS --&gt; TXT (ASCII) --&gt; EXE (how?)"
date: 2013-03-16
forum: Any Other OS
---

### Post by Larryes on 2013-03-16
Hi!

I want co compile GW-Basic's .BAS file into .EXE file. I converted my .BAS file into plain ASCII as mentioned here: [http://ubuntuforums.org/showthread.php?t=1959486&p=11860089#post11860089](http://ubuntuforums.org/showthread.php?t=1959486&p=11860089#post11860089)

Now I have no idea how to compile .TXT into .EXE... The program should stay DOS app, so windows compilers is not an option.

---

### Post by MAFoElffen on 2013-03-19
I used to do this. Not from Basic, but writing text files as assembler source... piping it through DOS debug to turn it into a binary. Then through link and exe2bin to make it into a DOS executable.

I wrote a utility in C and compiled it for use at a company. They said they couldn't use or maintain it because they didn't have a license for a C compiler.  So they thought there would be licensing issues.They had licenses for DOS. So I redid it as described above to suit their requirements. I'm wondering if that "dates" me... as that was about 20 years ago.

So look at those 3 DOS utilities: debug.exe, link.exe and exe2bin.exe.

The problem I see in your instance is that GWBasic and Basic ran interpreted  so the basic source code itself ran on an interpreter or a run-time (per-say)... So to extract it as an uninterpreted binary, or converted from Basic source to asm source to use those three utiltilites, you could use one of the old basic compilers (Remembering the Old MS Basic 6.0 compiler), that creates a binary (hex)...  then to disassemble into asm source, then create the DOS executable. As I remember right, I think there was options in the Basic Compilers to add in a run-time library when it compiled to create a stand-alone executable.

Or with the FreeBASIC Compiler, there is a DOS port...

---

### Post by coldraven on 2013-03-19
Find a copy of Borland's Turbo Basic. You can compile to an .exe directly from the editor.

---

### Post by lisati on 2013-03-19
Not Ubuntu related

*Thread moved to **Other OS/Distro Talk**.*

---

