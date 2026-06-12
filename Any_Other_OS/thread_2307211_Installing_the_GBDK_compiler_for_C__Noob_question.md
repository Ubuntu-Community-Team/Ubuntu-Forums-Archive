---
title: "Installing the GBDK compiler for C / Noob question"
date: 2015-12-22
forum: Any Other OS
---

### Post by whyigotta on 2015-12-22
I'm trying to install the gbdk gameboy c compiler from here: [http://sourceforge.net/projects/gbdk/?source=typ_redirect](http://sourceforge.net/projects/gbdk/?source=typ_redirect), which I think is the same as compiling the examples folder into a .gb file, but it's not working.

The Readme says " * Set GBDKDIR to where you installed with a trailing /" What does 'Set GBDKDIR' mean? What is GBDKDIR?

On other websites I found an instruction to type 'export GBDKDIR=$HOME/gbdk/' I have tried this, and I've tried to export GBDKDIR to the directory I installed it, but when I type that, terminal returns nothing. When I type 'make' in the gbdk/gb/examples directory, terminal returns 
'../../bin/lcc -Wa-l -Wl-m -Wl-j -DUSE_SFR_FOR_REG -c -o galaxy.o galaxy.c

../../bin/lcc: /home/User/Downloads/gbdkbin/sdcpp: No such file or directory

make: *** [galaxy.o] Error 1'

Can anyone help me with this please?

---

### Post by steeldriver on 2015-12-22
Based on this

```

../../bin/lcc: /home/User/Downloads/[COLOR=#ff0000]**gbdkbin**[/COLOR]/sdcpp: No such file or directory

```

I think you probably just missed the bit about the trailing slash i.e. you need

```

export GBDKDIR=/home/User/Downloads/gbdk[COLOR=#0000ff]**/**[/COLOR]

```

---

### Post by whyigotta on 2015-12-22
Unfortunately, no, I included the trailing slash. That was a typo in my original post, it should read "[COLOR=#000000][FONT=Ubuntu Mono]../../bin/lcc: /home/User/Downloads/gbdk/bin/[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sdcpp: No such file or directory"[/FONT][/COLOR]

---

### Post by steeldriver on 2015-12-22
Well perhaps you could tell us exactly where you did extract it to? For example if I'm in my $HOME/Downloads (which contains gbdk-2.96a-i586-pc-linux2.2.tar.gz) and I do

```

tar xf gbdk-2.96a-i586-pc-linux2.2.tar.gz

export GBDKDIR=$HOME/Downloads/gbdk/

cd $HOME/Downloads/gbdk/examples/gb

make

```

it all seems to  work

---

### Post by whyigotta on 2015-12-24
Thank you, I copied exactly what you did and it worked.

I initially downloaded the slightly earlier 2.95 version, which was also a tar.bz2 not a tar.gz. I also used the command [FONT=arial]tar jvxf instead of just tar xf. I used the same directories though. I don't know which of those slight differences caused the problem, but thanks for the help anyway.[/FONT]

---

