---
title: "Lightning Extension 1.0 for Linux PPC"
date: 2010-06-23
forum: Apple Hardware Users
---

### Post by cfabbriumd on 2010-06-23
I've upgraded my old PPC Ubuntu computer to Lucid and thus it upgraded to Thunderbird 3. The new version does not allow for the old Lightning extension, and the upgraded distro does not have the extension in it like the old one did.

My first though was to see if someone else built it. I didn't find anything, not for Lightning 1.0 anyway. Then I tried to build it. I downloaded the source code via Mozilla's instructions ([https://developer.mozilla.org/en/Comm-central_source_code_%28Mercurial%29](https://developer.mozilla.org/en/Comm-central_source_code_%28Mercurial%29)) and I tried to build Thunderbird with the extension (It wouldn't let me build just the extension)

About three minutes into the build, I get an assembly error message saying Error: junk at end of line, first unrecognized character is `@'

I tried different options including enabling the debugger and using only one CPU, but that did not result in anything.

I was wondering if someone has a PPC binary of the latest Lightning extension out there or be able to help with an error. This may be a lost cause, but maybe someone has it ](*,)

---

### Post by cfabbriumd on 2010-07-26
I just happened to come across an PPC RPM for Fedora for the extension. I extracted the contents of the package and zipped the extension and added a .xpi at the end of it. (One thing I learned today is that xpi packages are only zip files with certain installer files.) 

Anyway, I tried to install the add on into Thunderbird. Turns out that my Thunderbird was still too new for this version. Instead of searching aimlessly for another package, I went in and edited the install file to allow for a new version. I re-zipped it and PRESTO! I was able to get it to work. Finally!!!

For safe keeping, I put the Linux Lightning Extension on my server. If you are interested, you can download it at [http://cfabbri.dyndns.org/thunderbird-lightning-1.0-0.12.20090916hg.linux.ppc.xpi](http://cfabbri.dyndns.org/thunderbird-lightning-1.0-0.12.20090916hg.linux.ppc.xpi)

---

### Post by imrazor on 2010-07-26
> **cfabbriumd said:**
> I've upgraded my old PPC Ubuntu computer to Lucid and thus it upgraded to Thunderbird 3. The new version does not allow for the old Lightning extension, and the upgraded distro does not have the extension in it like the old one did.

My first though was to see if someone else built it. I didn't find anything, not for Lightning 1.0 anyway. Then I tried to build it. I downloaded the source code via Mozilla's instructions ([https://developer.mozilla.org/en/Comm-central_source_code_%28Mercurial%29](https://developer.mozilla.org/en/Comm-central_source_code_%28Mercurial%29)) and I tried to build Thunderbird with the extension (It wouldn't let me build just the extension)

About three minutes into the build, I get an assembly error message saying Error: junk at end of line, first unrecognized character is `@'

I tried different options including enabling the debugger and using only one CPU, but that did not result in anything.

I was wondering if someone has a PPC binary of the latest Lightning extension out there or be able to help with an error. This may be a lost cause, but maybe someone has it ](*,)

I've seen the junk at the end of the line referencing "@" when trying to compile ffmpeg from source. The only thing I can think of is that we're using the wrong assembler (or the wrong one is included in Ubuntu) and it can't parse the assembler source files. I worked around it by running ```
./configure (options) --disable-asm
``` If you find a fix for that, please let us know.

---

### Post by cfabbriumd on 2010-07-29
Naw, that didn't work. It's stopping at the same place and has the same error message. However, I was able to extract that package and that worked wonderfully, so I probably won't bother with that. Thanks for your help though. :-/

---

