---
title: "Installing tar.gz programs are a nightmare...."
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by Brightbelt on 2007-05-23
My apologies for being somewhat blunt, but the claims of ease in installing programs in Linux are somewhat exaggerated.  I'm a fairly smart guy - not a geek, mind you, but intelligent. 

Add/Remove is a breeze. So is the Synaptic Package Manager if your software is already in the repositories.  Anything else where you have to run code seems like an obstacle course. 
 
I'm trying to install a tar.gz program for my audio setup in Ubuntu Studio. I got the commands below from a beginner's tutorial. It didn't work. They never do. No Apt-get install command I have tried during the whole first 2 weeks in Ubuntu has EVER succeeded. 

I either get a response that the package can't be found (even though it's right there on my desktop) or that the directory can't be found. I've also already extracted the packages like I think you are supposed to. 

# tar -xzvf package-version.tar.gz
# cd package-version
# ./configure
# make
# make install 

I appreciate any help or assistance. I'm about to leave Ubuntu Studio unless it gets better really fast. I don't have time to spend hours trying to do an install. 

Code does not scare me; inconsistency does. Thanks, Frank

---

### Post by Bachstelze on 2007-05-23
Maybe it would help if you told us what exactly you are trying to install...

---

### Post by aysiu on 2007-05-23
> **Brightbelt said:**
> 
Add/Remove is a breeze. So is the Synaptic Package Manager if your software is already in the repositories.  Anything else where you have to run code seems like an obstacle course. > No Apt-get install command I have tried during the whole first 2 weeks in Ubuntu has EVER succeeded.  These two statements confuse me. Synaptic and Add/Remove are just graphical frontends for *apt-get* commands. Can you post the actual errors you're getting from the *apt-get* commands you're pasting into the terminal? > I either get a response that the package can't be found (even though it's right there on my desktop) or that the directory can't be found. Are you still talking about *apt-get* commands? *apt-get* (like Synaptic and Add/Remove, since they're all really the same thing) fetches software from online repositories, not your desktop.

I will agree with you, though, that compiling .tar.gz files from source is a pain. I've never (fortunately enough) *had* to compile a program from source. The few times I've tried to do it (just out of curiosity), I've never been successful.

---

### Post by Ek0nomik on 2007-05-23
tar.gz isn't an executable like a .exe or .msi in Windows.  It's a packaging format, like .zip, .tar, or .rar.

What do you mean an apt-get command hasn't worked?  What are you trying to install, and what errors are you getting?  An apt-get command just downloads from a server, but you need to make sure you have the package name correct.

Anyways, back to your tar.gz file you are working with.  Where is the file?  On your Desktop?

Load up a terminal and type:

```
sudo aptitude install build-essential
cd Desktop
tar -xzvf YOUR.FILE.NAME.HERE.tar.gz
cd YOUR.FILE.NAME.HERE
./configure
make
make install
```

build-essential provides you with the necessary library files to compile programs.  Without this, you probably can't compile most programs.  Other programs require addition dependencies, but we won't worry about that... yet.  Inside of YOUR.FILE.NAME.HERE, there should be a README file that you can read using nano, vim, or gedit (whatever your "text viewing" program of choice is).  There should be instructions in that, but in most cases they are similar to what you found.

---

### Post by aysiu on 2007-05-23
I think you should read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Bachstelze on 2007-05-23
Maybe it's just because I've been "in the business" for quite a while but I really can't understand why people find compiling so hard. I mean, just install b-e, download your source, extract, configure, make, make install, you're there ! While it is true that Ubuntu is not particularly "compile-friendly", it is still a fairly easy thing to do (for small software, I mean, recompiling X doesn't count :p).

---

### Post by aysiu on 2007-05-23
> **HymnToLife said:**
> Maybe it's just because I've been "in the business" for quite a while but I really can't understand why people find compiling so hard. I mean, just install b-e, download your source, extract, configure, make, make install, you're there ! While it is true that Ubuntu is not particularly "compile-friendly", it is still a fairly easy thing to do (for small software, I mean, recompiling X doesn't count :p).
Well, personally speaking, the few times I've tried to compile from source I haven't been able to track down all the dependencies and/or find the right versions of the dependencies I need... or the dependencies themselves have to be compiled because I can't find a .deb for it.

Sorry--*apt-get* for me.

---

### Post by Ek0nomik on 2007-05-23
> **HymnToLife said:**
> Maybe it's just because I've been "in the business" for quite a while but I really can't understand why people find compiling so hard. I mean, just install b-e, download your source, extract, configure, make, make install, you're there ! While it is true that Ubuntu is not particularly "compile-friendly", it is still a fairly easy thing to do (for small software, I mean, recompiling X doesn't count :p).

I have had both bad and good luck compiling from source.  I haven't done a lot of compiling, but I have done some.

If I have ever had bad luck compiling, it's always because I need a library file.  BUT, the README file doesn't list all the dependencies, which can be really frustrating.

---

### Post by Brightbelt on 2007-05-23
Ok, I think I'm making progress but I'm Not quite there. Btw, this is wineasio-0.1 audio driver for using Asio windows drivers in Ubuntu Studio. 

I think the build-essential part worked. (Is that a one time thing or should I do that for every tar.gz install?)

Now, I got to either the 'cd filename' part just before the './configure' or it was the './configure' where it said, 'There is no such directory'.

I think everything up to the configure part worked... Any ideas?

I appreciate any follow up help. Many Thanks, Frank

---

### Post by Bachstelze on 2007-05-23
No configure for it. Just

```
make
sudo make install
```

---

### Post by Brightbelt on 2007-05-23
OK, I get all the way to 'make',  and here's what I get:

brightbelt@brightbelt:~/Desktop$ cd wineasio-0.1
brightbelt@brightbelt:~/Desktop/wineasio-0.1$ make
gcc -c -I. -I/usr/include -I/usr/include -I/usr/include/wine -I/usr/include/wine/windows    -g -D__WINESRC__ -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith -o asio.o asio.c
asio.c:28:33: error: wine/windows/windef.h: No such file or directory
asio.c:29:34: error: wine/windows/winbase.h: No such file or directory
asio.c:30:34: error: wine/windows/objbase.h: No such file or directory
asio.c:31:35: error: wine/windows/mmsystem.h: No such file or directory
asio.c:37:26: error: wine/library.h: No such file or directory
asio.c:38:24: error: wine/debug.h: No such file or directory
asio.c:40:23: error: jack/jack.h: No such file or directory
asio.c:43:18: error: asio.h: No such file or directory
asio.c:45: warning: data definition has no type or storage class
asio.c:45: warning: type defaults to ‘int’ in declaration of ‘WINE_DEFAULT_DEBUG_CHANNEL’
asio.c:45: warning: parameter names (without types) in function declaration
asio.c:55: error: ‘jack_activate’ undeclared here (not in a function)
asio.c:55: warning: type defaults to ‘int’ in declaration of ‘fp_jack_activate’
asio.c:56: error: ‘jack_deactivate’ undeclared here (not in a function)
asio.c:56: warning: type defaults to ‘int’ in declaration of ‘fp_jack_deactivate’
asio.c:57: error: ‘jack_connect’ undeclared here (not in a function)
asio.c:57: warning: type defaults to ‘int’ in declaration of ‘fp_jack_connect’
asio.c:58: error: ‘jack_client_open’ undeclared here (not in a function)
asio.c:58: warning: type defaults to ‘int’ in declaration of ‘fp_jack_client_open’
asio.c:59: error: ‘jack_client_close’ undeclared here (not in a function)
asio.c:59: warning: type defaults to ‘int’ in declaration of ‘fp_jack_client_close’
asio.c:60: error: ‘jack_transport_query’ undeclared here (not in a function)
asio.c:60: warning: type defaults to ‘int’ in declaration of ‘fp_jack_transport_query’
asio.c:61: error: ‘jack_transport_start’ undeclared here (not in a function)
asio.c:61: warning: type defaults to ‘int’ in declaration of ‘fp_jack_transport_start’
asio.c:62: error: ‘jack_set_process_callback’ undeclared here (not in a function)
asio.c:62: warning: type defaults to ‘int’ in declaration of ‘fp_jack_set_process_callback’
asio.c:63: error: ‘jack_get_sample_rate’ undeclared here (not in a function)
asio.c:63: warning: type defaults to ‘int’ in declaration of ‘fp_jack_get_sample_rate’
asio.c:64: error: ‘jack_port_register’ undeclared here (not in a function)
asio.c:64: warning: type defaults to ‘int’ in declaration of ‘fp_jack_port_register’
asio.c:65: error: ‘jack_port_get_buffer’ undeclared here (not in a function)
asio.c:65: warning: type defaults to ‘int’ in declaration of ‘fp_jack_port_get_buffer’
asio.c:66: error: ‘jack_get_ports’ undeclared here (not in a function)
asio.c:66: warning: type defaults to ‘int’ in declaration of ‘fp_jack_get_ports’
asio.c:67: error: ‘jack_port_name’ undeclared here (not in a function)
asio.c:67: warning: type defaults to ‘int’ in declaration of ‘fp_jack_port_name’
asio.c:68: error: ‘jack_get_buffer_size’ undeclared here (not in a function)
asio.c:68: warning: type defaults to ‘int’ in declaration of ‘fp_jack_get_buffer_size’
asio.c:74: error: expected ‘)’ before ‘nframes’
asio.c:77: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘CALLBACK’
asio.c:80: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘const’
asio.c:123: warning: return type defaults to ‘int’
asio.c: In function ‘DECLARE_INTERFACE_’:
asio.c:124: warning: implicit declaration of function ‘STDMETHOD_’
asio.c:124: error: ‘HRESULT’ undeclared (first use in this function)
asio.c:124: error: (Each undeclared identifier is reported only once
asio.c:124: error: for each function it appears in.)
asio.c:124: error: ‘QueryInterface’ undeclared (first use in this function)
asio.c:124: error: ‘THIS_’ undeclared (first use in this function)
asio.c:124: error: expected ‘)’ before ‘REFIID’
asio.c:124: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:124: error: expected ‘;’ before ‘PURE’
asio.c:125: error: ‘ULONG’ undeclared (first use in this function)
asio.c:125: error: ‘AddRef’ undeclared (first use in this function)
asio.c:125: error: ‘THIS’ undeclared (first use in this function)
asio.c:125: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:125: error: expected ‘;’ before ‘PURE’
asio.c:126: error: ‘Release’ undeclared (first use in this function)
asio.c:126: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:126: error: expected ‘;’ before ‘PURE’
asio.c:127: error: expected expression before ‘long’
asio.c:127: error: expected ‘)’ before ‘void’
asio.c:127: error: called object ‘STDMETHOD_(<erroneous-expression>)’ is not a function
asio.c:127: error: expected ‘;’ before ‘PURE’
asio.c:128: error: expected expression before ‘void’
asio.c:128: error: expected ‘)’ before ‘char’
asio.c:128: error: called object ‘STDMETHOD_(<erroneous-expression>)’ is not a function
asio.c:128: error: expected ‘;’ before ‘PURE’
asio.c:129: error: expected expression before ‘long’
asio.c:129: error: called object ‘STDMETHOD_(<erroneous-expression>)’ is not a function
asio.c:129: error: expected ‘;’ before ‘PURE’
asio.c:130: error: expected expression before ‘void’
asio.c:130: error: expected ‘)’ before ‘char’
asio.c:130: error: called object ‘STDMETHOD_(<erroneous-expression>)’ is not a function
asio.c:130: error: expected ‘;’ before ‘PURE’
asio.c:131: error: ‘ASIOError’ undeclared (first use in this function)
asio.c:131: error: ‘start’ undeclared (first use in this function)
asio.c:131: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:131: error: expected ‘;’ before ‘PURE’
asio.c:132: error: ‘stop’ undeclared (first use in this function)
asio.c:132: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:132: error: expected ‘;’ before ‘PURE’
asio.c:133: error: ‘getChannels’ undeclared (first use in this function)
asio.c:133: error: expected ‘)’ before ‘long’
asio.c:133: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:133: error: expected ‘;’ before ‘PURE’
asio.c:134: error: ‘getLatencies’ undeclared (first use in this function)
asio.c:134: error: expected ‘)’ before ‘long’
asio.c:134: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:134: error: expected ‘;’ before ‘PURE’
asio.c:135: error: ‘getBufferSize’ undeclared (first use in this function)
asio.c:135: error: expected ‘)’ before ‘long’
asio.c:135: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:135: error: expected ‘;’ before ‘PURE’
asio.c:136: error: ‘canSampleRate’ undeclared (first use in this function)
asio.c:136: error: expected ‘)’ before ‘ASIOSampleRate’
asio.c:136: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:136: error: expected ‘;’ before ‘PURE’
asio.c:137: error: ‘getSampleRate’ undeclared (first use in this function)
asio.c:137: error: expected ‘)’ before ‘ASIOSampleRate’
asio.c:137: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:137: error: expected ‘;’ before ‘PURE’
asio.c:138: error: ‘setSampleRate’ undeclared (first use in this function)
asio.c:138: error: expected ‘)’ before ‘ASIOSampleRate’
asio.c:138: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:138: error: expected ‘;’ before ‘PURE’
asio.c:139: error: ‘getClockSources’ undeclared (first use in this function)
asio.c:139: error: expected ‘)’ before ‘ASIOClockSource’
asio.c:139: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:139: error: expected ‘;’ before ‘PURE’
asio.c:140: error: ‘setClockSource’ undeclared (first use in this function)
asio.c:140: error: expected ‘)’ before ‘long’
asio.c:140: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:140: error: expected ‘;’ before ‘PURE’
asio.c:141: error: ‘getSamplePosition’ undeclared (first use in this function)
asio.c:141: error: expected ‘)’ before ‘ASIOSamples’
asio.c:141: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:141: error: expected ‘;’ before ‘PURE’
asio.c:142: error: ‘getChannelInfo’ undeclared (first use in this function)
asio.c:142: error: expected ‘)’ before ‘ASIOChannelInfo’
asio.c:142: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:142: error: expected ‘;’ before ‘PURE’
asio.c:143: error: ‘createBuffers’ undeclared (first use in this function)
asio.c:143: error: expected ‘)’ before ‘ASIOBufferInfo’
asio.c:143: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:143: error: expected ‘;’ before ‘PURE’
asio.c:144: error: ‘disposeBuffers’ undeclared (first use in this function)
asio.c:144: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:144: error: expected ‘;’ before ‘PURE’
asio.c:145: error: ‘controlPanel’ undeclared (first use in this function)
asio.c:145: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:145: error: expected ‘;’ before ‘PURE’
asio.c:146: error: ‘future’ undeclared (first use in this function)
asio.c:146: error: expected ‘)’ before ‘long’
asio.c:146: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:146: error: expected ‘;’ before ‘PURE’
asio.c:147: error: ‘outputReady’ undeclared (first use in this function)
asio.c:147: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:147: error: expected ‘;’ before ‘PURE’
asio.c:148: warning: control reaches end of non-void function
asio.c: At top level:
asio.c:161: error: expected specifier-qualifier-list before ‘ASIOBool’
asio.c:169: error: expected ‘:’, ‘,’, ‘;’, ‘}’ or ‘__attribute__’ before ‘*’ token
asio.c:208: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘WINAPI’
asio.c:215: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘WINAPI’
asio.c:240: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘WINAPI’
asio.c:257: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:257: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:364: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_getDriverName’
asio.c:364: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_getDriverName’
asio.c:369: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_getDriverVersion’
asio.c:369: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_getDriverVersion’
asio.c:374: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_getErrorMessage’
asio.c:374: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_getErrorMessage’
asio.c:379: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:379: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:439: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:439: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:453: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:453: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:465: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:465: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:477: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:477: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:495: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:495: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:504: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:504: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:513: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:513: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:522: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:522: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:540: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:540: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:553: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:553: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:573: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:573: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:601: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:601: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:621: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:621: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:702: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:702: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:708: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:708: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:732: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:732: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:737: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘WineASIO_Vtbl’
asio.c:765: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘init_jack’
asio.c:807: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘asioCreateInstance’
asio.c:820: error: expected ‘)’ before ‘*’ token
asio.c:827: error: expected ‘)’ before ‘nframes’
asio.c:891: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘CALLBACK’
make: *** [asio.o] Error 1
brightbelt@brightbelt:~/Desktop/wineasio-0.1$ make install
cp wineasio.dll.so /usr/lib/wine
cp: cannot stat `wineasio.dll.so': No such file or directory
make: *** [install] Error 1
brightbelt@brightbelt:~/Desktop/wineasio-0.1$

---

### Post by aysiu on 2007-05-23
According to [this tutorial](http://www.davehayes.org/2007/04/27/howto-reaper-on-ubuntu-linux-with-wineasio/), you should copy and paste these commands: ```
sudo apt-get update
sudo apt-get -y install wine wine-dev libjack0.100.0-dev qjackctl build-essential linux-lowlatency
cd ~/Desktop
wget -c http://people.jacklab.net/edogawa/files/wineasio/wineasio-0.1.tar.gz
``` Download Steinberg asio-sdk from [here](http://www.steinberg.net/329+M52087573ab0.html) to your desktop.

Then, continue with these commands: ```
tar zxvf wineasio-0.1.tar.gz
unzip asiosdk2.2.zip
cd wineasio-0.1
cp ../ASIOSDK2/common/asio.h .
make
sudo make install
regsvr32 wineasio.dll
sudo ln -s /usr/lib/libjack-0.100.0.so.0 /usr/lib/libjack.so.0
winecfg
```

---

### Post by Alterax on 2007-05-23
No, it won't be necessary to do an apt-get install for build-essential every time.

build-essential is just a package of libraries, compilers, and handy tools that make compiling programs easier.  It stays on your computer (unless you remove it).

Enjoy.  It usually takes a bit to get started, but I have a feeling you'll get the hang of installing from source in no time.

--Alterax

---

### Post by Brightbelt on 2007-05-23
OK, I get all the way to 'make' and then I get this:

brightbelt@brightbelt:~/Desktop/wineasio-0.1$ make
gcc -c -I. -I/usr/include -I/usr/include -I/usr/include/wine -I/usr/include/wine/windows    -g -D__WINESRC__ -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith -o asio.o asio.c
asio.c:28:33: error: wine/windows/windef.h: No such file or directory
asio.c:29:34: error: wine/windows/winbase.h: No such file or directory
asio.c:30:34: error: wine/windows/objbase.h: No such file or directory
asio.c:31:35: error: wine/windows/mmsystem.h: No such file or directory
asio.c:37:26: error: wine/library.h: No such file or directory
asio.c:38:24: error: wine/debug.h: No such file or directory
asio.c:40:23: error: jack/jack.h: No such file or directory
asio.c:43:18: error: asio.h: No such file or directory
asio.c:45: warning: data definition has no type or storage class
asio.c:45: warning: type defaults to ‘int’ in declaration of ‘WINE_DEFAULT_DEBUG_CHANNEL’
asio.c:45: warning: parameter names (without types) in function declaration
asio.c:55: error: ‘jack_activate’ undeclared here (not in a function)
asio.c:55: warning: type defaults to ‘int’ in declaration of ‘fp_jack_activate’
asio.c:56: error: ‘jack_deactivate’ undeclared here (not in a function)
asio.c:56: warning: type defaults to ‘int’ in declaration of ‘fp_jack_deactivate’
asio.c:57: error: ‘jack_connect’ undeclared here (not in a function)
asio.c:57: warning: type defaults to ‘int’ in declaration of ‘fp_jack_connect’
asio.c:58: error: ‘jack_client_open’ undeclared here (not in a function)
asio.c:58: warning: type defaults to ‘int’ in declaration of ‘fp_jack_client_open’
asio.c:59: error: ‘jack_client_close’ undeclared here (not in a function)
asio.c:59: warning: type defaults to ‘int’ in declaration of ‘fp_jack_client_close’
asio.c:60: error: ‘jack_transport_query’ undeclared here (not in a function)
asio.c:60: warning: type defaults to ‘int’ in declaration of ‘fp_jack_transport_query’
asio.c:61: error: ‘jack_transport_start’ undeclared here (not in a function)
asio.c:61: warning: type defaults to ‘int’ in declaration of ‘fp_jack_transport_start’
asio.c:62: error: ‘jack_set_process_callback’ undeclared here (not in a function)
asio.c:62: warning: type defaults to ‘int’ in declaration of ‘fp_jack_set_process_callback’
asio.c:63: error: ‘jack_get_sample_rate’ undeclared here (not in a function)
asio.c:63: warning: type defaults to ‘int’ in declaration of ‘fp_jack_get_sample_rate’
asio.c:64: error: ‘jack_port_register’ undeclared here (not in a function)
asio.c:64: warning: type defaults to ‘int’ in declaration of ‘fp_jack_port_register’
asio.c:65: error: ‘jack_port_get_buffer’ undeclared here (not in a function)
asio.c:65: warning: type defaults to ‘int’ in declaration of ‘fp_jack_port_get_buffer’
asio.c:66: error: ‘jack_get_ports’ undeclared here (not in a function)
asio.c:66: warning: type defaults to ‘int’ in declaration of ‘fp_jack_get_ports’
asio.c:67: error: ‘jack_port_name’ undeclared here (not in a function)
asio.c:67: warning: type defaults to ‘int’ in declaration of ‘fp_jack_port_name’
asio.c:68: error: ‘jack_get_buffer_size’ undeclared here (not in a function)
asio.c:68: warning: type defaults to ‘int’ in declaration of ‘fp_jack_get_buffer_size’
asio.c:74: error: expected ‘)’ before ‘nframes’
asio.c:77: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘CALLBACK’
asio.c:80: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘const’
asio.c:123: warning: return type defaults to ‘int’
asio.c: In function ‘DECLARE_INTERFACE_’:
asio.c:124: warning: implicit declaration of function ‘STDMETHOD_’
asio.c:124: error: ‘HRESULT’ undeclared (first use in this function)
asio.c:124: error: (Each undeclared identifier is reported only once
asio.c:124: error: for each function it appears in.)
asio.c:124: error: ‘QueryInterface’ undeclared (first use in this function)
asio.c:124: error: ‘THIS_’ undeclared (first use in this function)
asio.c:124: error: expected ‘)’ before ‘REFIID’
asio.c:124: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:124: error: expected ‘;’ before ‘PURE’
asio.c:125: error: ‘ULONG’ undeclared (first use in this function)
asio.c:125: error: ‘AddRef’ undeclared (first use in this function)
asio.c:125: error: ‘THIS’ undeclared (first use in this function)
asio.c:125: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:125: error: expected ‘;’ before ‘PURE’
asio.c:126: error: ‘Release’ undeclared (first use in this function)
asio.c:126: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:126: error: expected ‘;’ before ‘PURE’
asio.c:127: error: expected expression before ‘long’
asio.c:127: error: expected ‘)’ before ‘void’
asio.c:127: error: called object ‘STDMETHOD_(<erroneous-expression>)’ is not a function
asio.c:127: error: expected ‘;’ before ‘PURE’
asio.c:128: error: expected expression before ‘void’
asio.c:128: error: expected ‘)’ before ‘char’
asio.c:128: error: called object ‘STDMETHOD_(<erroneous-expression>)’ is not a function
asio.c:128: error: expected ‘;’ before ‘PURE’
asio.c:129: error: expected expression before ‘long’
asio.c:129: error: called object ‘STDMETHOD_(<erroneous-expression>)’ is not a function
asio.c:129: error: expected ‘;’ before ‘PURE’
asio.c:130: error: expected expression before ‘void’
asio.c:130: error: expected ‘)’ before ‘char’
asio.c:130: error: called object ‘STDMETHOD_(<erroneous-expression>)’ is not a function
asio.c:130: error: expected ‘;’ before ‘PURE’
asio.c:131: error: ‘ASIOError’ undeclared (first use in this function)
asio.c:131: error: ‘start’ undeclared (first use in this function)
asio.c:131: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:131: error: expected ‘;’ before ‘PURE’
asio.c:132: error: ‘stop’ undeclared (first use in this function)
asio.c:132: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:132: error: expected ‘;’ before ‘PURE’
asio.c:133: error: ‘getChannels’ undeclared (first use in this function)
asio.c:133: error: expected ‘)’ before ‘long’
asio.c:133: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:133: error: expected ‘;’ before ‘PURE’
asio.c:134: error: ‘getLatencies’ undeclared (first use in this function)
asio.c:134: error: expected ‘)’ before ‘long’
asio.c:134: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:134: error: expected ‘;’ before ‘PURE’
asio.c:135: error: ‘getBufferSize’ undeclared (first use in this function)
asio.c:135: error: expected ‘)’ before ‘long’
asio.c:135: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:135: error: expected ‘;’ before ‘PURE’
asio.c:136: error: ‘canSampleRate’ undeclared (first use in this function)
asio.c:136: error: expected ‘)’ before ‘ASIOSampleRate’
asio.c:136: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:136: error: expected ‘;’ before ‘PURE’
asio.c:137: error: ‘getSampleRate’ undeclared (first use in this function)
asio.c:137: error: expected ‘)’ before ‘ASIOSampleRate’
asio.c:137: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:137: error: expected ‘;’ before ‘PURE’
asio.c:138: error: ‘setSampleRate’ undeclared (first use in this function)
asio.c:138: error: expected ‘)’ before ‘ASIOSampleRate’
asio.c:138: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:138: error: expected ‘;’ before ‘PURE’
asio.c:139: error: ‘getClockSources’ undeclared (first use in this function)
asio.c:139: error: expected ‘)’ before ‘ASIOClockSource’
asio.c:139: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:139: error: expected ‘;’ before ‘PURE’
asio.c:140: error: ‘setClockSource’ undeclared (first use in this function)
asio.c:140: error: expected ‘)’ before ‘long’
asio.c:140: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:140: error: expected ‘;’ before ‘PURE’
asio.c:141: error: ‘getSamplePosition’ undeclared (first use in this function)
asio.c:141: error: expected ‘)’ before ‘ASIOSamples’
asio.c:141: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:141: error: expected ‘;’ before ‘PURE’
asio.c:142: error: ‘getChannelInfo’ undeclared (first use in this function)
asio.c:142: error: expected ‘)’ before ‘ASIOChannelInfo’
asio.c:142: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:142: error: expected ‘;’ before ‘PURE’
asio.c:143: error: ‘createBuffers’ undeclared (first use in this function)
asio.c:143: error: expected ‘)’ before ‘ASIOBufferInfo’
asio.c:143: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:143: error: expected ‘;’ before ‘PURE’
asio.c:144: error: ‘disposeBuffers’ undeclared (first use in this function)
asio.c:144: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:144: error: expected ‘;’ before ‘PURE’
asio.c:145: error: ‘controlPanel’ undeclared (first use in this function)
asio.c:145: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:145: error: expected ‘;’ before ‘PURE’
asio.c:146: error: ‘future’ undeclared (first use in this function)
asio.c:146: error: expected ‘)’ before ‘long’
asio.c:146: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:146: error: expected ‘;’ before ‘PURE’
asio.c:147: error: ‘outputReady’ undeclared (first use in this function)
asio.c:147: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:147: error: expected ‘;’ before ‘PURE’
asio.c:148: warning: control reaches end of non-void function
asio.c: At top level:
asio.c:161: error: expected specifier-qualifier-list before ‘ASIOBool’
asio.c:169: error: expected ‘:’, ‘,’, ‘;’, ‘}’ or ‘__attribute__’ before ‘*’ token
asio.c:208: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘WINAPI’
asio.c:215: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘WINAPI’
asio.c:240: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘WINAPI’
asio.c:257: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:257: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:364: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_getDriverName’
asio.c:364: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_getDriverName’
asio.c:369: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_getDriverVersion’
asio.c:369: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_getDriverVersion’
asio.c:374: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_getErrorMessage’
asio.c:374: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_getErrorMessage’
asio.c:379: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:379: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:439: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:439: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:453: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:453: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:465: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:465: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:477: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:477: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:495: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:495: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:504: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:504: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:513: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:513: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:522: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:522: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:540: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:540: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:553: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:553: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:573: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:573: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:601: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:601: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:621: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:621: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:702: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:702: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:708: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:708: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:732: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:732: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__stdcall’
asio.c:737: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘WineASIO_Vtbl’
asio.c:765: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘init_jack’
asio.c:807: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘asioCreateInstance’
asio.c:820: error: expected ‘)’ before ‘*’ token
asio.c:827: error: expected ‘)’ before ‘nframes’
asio.c:891: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘CALLBACK’
make: *** [asio.o] Error 1
brightbelt@brightbelt:~/Desktop/wineasio-0.1$

---

### Post by Bachstelze on 2007-05-23
Are you sure you installed wine-dev ?

---

### Post by Brightbelt on 2007-05-23
Here's what I got Aysiu; there are errors but did this work or not?

brightbelt@brightbelt:~/wineasio-0.1$ sudo make install
cp wineasio.dll.so /usr/lib/wine
cp: cannot stat `wineasio.dll.so': No such file or directory
make: *** [install] Error 1
brightbelt@brightbelt:~/wineasio-0.1$ regsvr32 wineasio.dll
wine: creating configuration directory '/home/brightbelt/.wine'...
wine: '/home/brightbelt/.wine' created successfully.
Failed to load DLL wineasio.dll
brightbelt@brightbelt:~/wineasio-0.1$ sudo ln -s /usr/lib/libjack-0.100.0.so.0 /usr/lib/libjack.so.0
brightbelt@brightbelt:~/wineasio-0.1$ winecfg

---

### Post by Bachstelze on 2007-05-23
Don't do sudo make install until make finished successfully.

---

### Post by Brightbelt on 2007-05-23
OK, I realized - paste and run 1 line at a time !!

I think this worked !! How did you find all that code Aysiu???? Were there instuctions somewhere online?

Many Thanks for all your help. I think this driver should run my Mackie Onyx 1620, since it uses Asio drivers.

Thanks again, Frank

---

