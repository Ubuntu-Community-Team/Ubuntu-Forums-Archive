---
title: "Banshee not opening......"
date: 2012-06-09
forum: Any Other OS
---

### Post by abnordude on 2012-06-09
I'll explain in detail.....

I am using arch.....
I did a virus scan using clamtk....
Well.....I found a bunch.....no.....a hell of viruses......
The files that were affected were the wine files......(exe)
Among them there were also a few .dll files too......
I deleted all of the infected files...
Then now...when i open banshee through the terminal....I get an error message saying that a .dll file was missing.....(dunno what .dll file it was.....
So, i did a search and got to reinstalling mono....
Now when i launch banshee from the terminal....I get.....

Unhandled Exception: System.TypeLoadException: A type load exception has occurred.
  at Booter.Booter.Main () [0x00000] in <filename unknown>:0 
[ERROR] FATAL UNHANDLED EXCEPTION: System.TypeLoadException: A type load exception has occurred.
  at Booter.Booter.Main () [0x00000] in <filename unknown>:0 

Please help me guys......

---

### Post by abnordude on 2012-06-09
Also....Tomboy doesn't seem to be opening too.....

---

### Post by chamber on 2012-06-09
```
pacman -R banshee tomboy
pacman -R tomboy
pacman -Syyu
pacman -S banshee tomboy 
```

Don't remove random files without knowing what they are.

---

### Post by abnordude on 2012-06-10
> **chamber said:**
> ```
pacman -R banshee tomboy
pacman -R tomboy
pacman -Syyu
pacman -S banshee tomboy 
```Don't remove random files without knowing what they are.

Did that......still I get the same error

---

### Post by abnordude on 2012-06-10
Ah yes i forgot to add.....
I'm getting that same old error

The assembly mscorlib.dll was not found or could not be loaded.
It should have been installed in the `/usr/lib/mono/2.0/mscorlib.dll' directory.

Maybe I've made things worse.....but i'll exlpain what I did.....

See, i did a reinstall of mono.....

Thats when I started getting this error:
Unhandled Exception: System.TypeLoadException: A type load exception has occurred.
  at Booter.Booter.Main () [0x00000] in <filename unknown>:0 
[ERROR] FATAL UNHANDLED EXCEPTION: System.TypeLoadException: A type load exception has occurred.
  at Booter.Booter.Main () [0x00000] in <filename unknown>:0 

Then when I scanned with clamtk, i got some viruses (again) in some .exe and some .dll files (which i removed again.....(Stupid.....I know)

Now when i try banshee frm the terminal, I get the first error:
The assembly mscorlib.dll was not found or could not be loaded.
It should have been installed in the `/usr/lib/mono/2.0/mscorlib.dll' directory.

I know I screwed things up.........AAAHhhhhhh.......I hate me...............

---

### Post by chamber on 2012-06-10
You must have also removed some of the dependencies. You need to figure out what those were. 

As I said before don't blindly remove files.

---

### Post by abnordude on 2012-06-10
Also...here is the history of the files scanned.....(only a few out of the 300+ files....)

/usr/lib/mono/gac/System.Design/2.0.0.0__b03f5f7f11d50a3a/System.Design.dll                                                                    PUA.Win32.Packer.NetExecutable       
/usr/lib/mono/gac/System.Design/4.0.0.0__b03f5f7f11d50a3a/System.Design.dll                                                                    PUA.Win32.Packer.NetExecutable       
/usr/lib/mono/gac/System.Drawing.Design/2.0.0.0__b03f5f7f11d50a3a/System.Drawing.Design.dll                                                    PUA.Win32.Packer.Net                 
/usr/lib/mono/gac/System.Drawing.Design/4.0.0.0__b03f5f7f11d50a3a/System.Drawing.Design.dll                                                    PUA.Win32.Packer.Net                 
/usr/lib/mono/gac/OpenSystem.C/4.0.0.0__b77a5c561934e089/OpenSystem.C.dll                                                                      PUA.Win32.Packer.Net                 
/usr/lib/mono/gac/OpenSystem.C/2.0.0.0__b77a5c561934e089/OpenSystem.C.dll                                                                      PUA.Win32.Packer.Net                 
/usr/lib/mono/gac/Mono.Debugger.Soft/2.0.0.0__0738eb9f132ed756/Mono.Debugger.Soft.dll                                                          PUA.Win32.Packer.NetExecutable       
/usr/lib/mono/gac/Mono.Debugger.Soft/4.0.0.0__0738eb9f132ed756/Mono.Debugger.Soft.dll                                                          PUA.Win32.Packer.NetExecutable       
/usr/lib/mono/gac/Mono.Simd/2.0.0.0__0738eb9f132ed756/Mono.Simd.dll                                                                            PUA.Win32.Packer.NetExecutable

Also Some filed with                                                                             PUA.Win32.Packer.NetExecutable-1

---

### Post by chamber on 2012-06-10
Linux viruses are very rare. And for you to have that many suggests you were seeing heaps of false positives or you used some cracked software in wine. 

You can try to restore the files and see if that helps, but who knows what other damage you have done.

---

### Post by abnordude on 2012-06-10
> **chamber said:**
> Linux viruses are very rare. And for you to have that many suggests you were seeing heaps of false positives or you used some cracked software in wine. 

You can try to restore the files and see if that helps, but who knows what other damage you have done.

Yes.....I was using cracked software in wine....But it was way back..........

I also noticed that all the affected files were from a folder called mono.......

What should i do now?

---

### Post by abnordude on 2012-06-10
Okay.....so i went into the mono folder...and i found some files that had extensions like

.exe.mdb......

My opinion is that I delete all the files from mono and reinstall mono.....

Is that okay????

---

### Post by chamber on 2012-06-10
I would have thought that you would have learned by now not to blindly delete files, this is how you got yourself into this mess. 

You can use pacman to let you know what package owns those files and reinstall it. 

pacman -Qo /path/to/a/file

As you have admitted to using cracked software your on your own now as I make it a point not to help in cases like this.

---

### Post by abnordude on 2012-06-13
> **chamber said:**
> I would have thought that you would have learned by now not to blindly delete files, this is how you got yourself into this mess. 

You can use pacman to let you know what package owns those files and reinstall it. 

pacman -Qo /path/to/a/file

As you have admitted to using cracked software your on your own now as I make it a point not to help in cases like this.

Okay...I'm admitting that I have used cracked softwares....But that was way back, when I was using debian in another partition (not in arch).....Also, after that, i started hating M!cro$oft and removed all the windows related things, (also wine)....All this happened way back

---

### Post by abnordude on 2012-06-13
Aahhh......
It had nothing to do with any viruses
PUA = Potntially Unwanted Applications.....They need not be viruses (meybe....idk).....
So, when I disabled extra scan settings, it didn't detect anything......

Okay.......
So, now i'm back to the same problem...

I get this when I try to lauch banshee from the terminal.....

Unhandled Exception: System.TypeLoadException: Could not load type 'Banshee.ServiceStack.DBusServiceManager' from assembly 'Banshee.Services, Version=2.4.0.0, Culture=neutral, PublicKeyToken=null'.
[ERROR] FATAL UNHANDLED EXCEPTION: System.TypeLoadException: Could not load type 'Banshee.ServiceStack.DBusServiceManager' from assembly 'Banshee.Services, Version=2.4.0.0, Culture=neutral, PublicKeyToken=null'.

---

### Post by chamber on 2012-06-13
You've messed up the dependencies from Banshee.

Remove banshee with the switch to remove Banshee and the dependencies and then re install Banshee.

---

### Post by abnordude on 2012-06-17
> **chamber said:**
> You've messed up the dependencies from Banshee.

Remove banshee with the switch to remove Banshee and the dependencies and then re install Banshee.

Sorry for taking this long to reply, but I was a bit busy with my college admissions.....

Yes, I tried reinstalling Banshee, yet I get the same error.....

---

### Post by chamber on 2012-06-17
How did you remove banshee and then re install it. 

Post the exact commands used.

---

### Post by abnordude on 2012-06-17
i just did a pacman -S banshee......
it said reinstall.....
i gave yes...

---

### Post by chamber on 2012-06-17
> **chamber said:**
> 
Remove banshee with the switch to remove Banshee and the dependencies and then re install Banshee.

You didn't actually do as I suggested.

---

### Post by abnordude on 2012-06-17
> **chamber said:**
> ```
pacman -R banshee tomboy
pacman -R tomboy
pacman -Syyu
pacman -S banshee tomboy 
```Don't remove random files without knowing what they are.
i also did this....this is a part of the words in terminal.....

Total Installed Size:   29.22 MiB

Proceed with installation? [Y/n] y
(2/2) checking package integrity                   [######################] 100%
(2/2) loading package files                        [######################] 100%
(2/2) checking for file conflicts                  [######################] 100%
(2/2) checking available disk space                [######################] 100%
(1/2) installing banshee                           [######################] 100%
Optional dependencies for banshee
    gstreamer0.10-good-plugins: Extra media codecs
    gstreamer0.10-ugly-plugins: Extra media codecs
    gstreamer0.10-ffmpeg: Extra media codecs
    brasero: CD burning
(2/2) installing tomboy                            [######################] 100%
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'


install is succesfull....but same error.....

---

### Post by chamber on 2012-06-17
Try pacman -Rs to remove dependencies. And then reinstall.

---

### Post by abnordude on 2012-06-18
> **chamber said:**
> Try pacman -Rs to remove dependencies. And then reinstall.

Tried doing it that way.....Still the same error.......

Unhandled Exception: System.TypeLoadException: A type load exception has occurred.
  at Booter.Booter.Main () [0x00000] in <filename unknown>:0 
[ERROR] FATAL UNHANDLED EXCEPTION: System.TypeLoadException: A type load exception has occurred.
  at Booter.Booter.Main () [0x00000] in <filename unknown>:0

---

### Post by abnordude on 2012-06-18
If it helps, here is the details of the banshee file in /usr/bin...

#!/usr/bin/env bash

prefix=/usr
libdir=/usr/lib
exec_asm="Banshee.exe"
MONO_EXE="/usr/lib/banshee/$exec_asm"
BANSHEE_EXEC_NAME=$(basename $0)
BANSHEE_CONFIG_DIR="${XDG_CONFIG_HOME:-$HOME/.config}/banshee-1"

export LD_LIBRARY_PATH=/usr/lib/banshee:/usr/lib/banshee/Extensions:/usr/lib/banshee/Backends:/usr/lib${LD_LIBRARY_PATH:+:$LD_LIBRARY_PATH}
export GST_PLUGIN_PATH=/usr/lib/banshee/gstreamer-0.10${GST_PLUGIN_PATH:+:$GST_PLUGIN_PATH}
if [ $BANSHEE_EXEC_NAME = "muinshee" ]; then
    BANSHEE_CLIENT="Muinshee"
    export MONO_PATH=/usr/lib/banshee/Extensions
fi

[ -n "$BANSHEE_DEBUG" -o -f "${BANSHEE_CONFIG_DIR}/always-debug" ] && BANSHEE_DEBUG="--debug"
[ -n "$BANSHEE_TRACE" ] && BANSHEE_TRACE="--trace=$BANSHEE_TRACE"
[ -n "$BANSHEE_PROFILE" ] && BANSHEE_PROFILE="--profile=$BANSHEE_PROFILE"

for arg in $*; do
    case "x--debug" in ("x$arg")
        BANSHEE_DEBUG=$arg
    esac

    case "x--trace=" in ("x${arg:0:8}")
        BANSHEE_TRACE=$arg
    esac

    case "x--profile=" in ("x${arg:0:10}")
        BANSHEE_PROFILE=$arg
    esac

    case "x--redirect-log" in ("x$arg")
        [ -z "$(pidof $BANSHEE_EXEC_NAME)" ] && BANSHEE_REDIRECT_LOG="${BANSHEE_CONFIG_DIR}/log"
    esac

    case "x--client=" in ("x${arg:0:9}")
        BANSHEE_CLIENT="${arg:9}"
    esac
done

if [ ! -z "$BANSHEE_CLIENT" ]; then
    BANSHEE_CLIENT="--client=${BANSHEE_CLIENT}"
fi

# We were testing the SGen compacting GC; disabled for 2.0 release b/c there are serious
# issues with sgen on Mono 2.8.0
#export MONO_ENV_OPTIONS="--gc=sgen"

if [ -n "$BANSHEE_DEBUG" -o -n "$BANSHEE_TRACE" -o -n "$BANSHEE_PROFILE" ]; then
    MONO_OPTIONS="$BANSHEE_DEBUG $BANSHEE_TRACE $BANSHEE_PROFILE"
    echo "** Running Mono with $MONO_OPTIONS **"
fi

# Finally - environment is set up, time to run our beloved
exec_args="-a $BANSHEE_EXEC_NAME mono $MONO_OPTIONS $MONO_EXE $BANSHEE_DEBUG $BANSHEE_CLIENT"

if [ -z "$BANSHEE_REDIRECT_LOG" ]; then
    exec $exec_args "$@"
else
    mkdir -p `dirname "$BANSHEE_REDIRECT_LOG"`
    (echo "exec $exec_args " "$@"; echo; exec $exec_args "$@") &> $BANSHEE_REDIRECT_LOG
fi

---

### Post by chamber on 2012-06-18
Run banshee from the command prompt

```
banshee --debug-addins
```

and 

```
banshee --debug
```

Please use code tags when pasting the output.

---

### Post by abnordude on 2012-06-18
> **chamber said:**
> Run banshee from the command prompt

```
banshee --debug-addins
```and 

```
banshee --debug
```Please use code tags when pasting the output.

'banshee --debug' gives...

** Running Mono with --debug   **

Unhandled Exception: System.TypeLoadException: A type load exception has occurred.
  at Booter.Booter.Main () [0x00010] in /build/src/banshee-2.4.1/src/Clients/Booter/Booter/Entry.cs:82 
[ERROR] FATAL UNHANDLED EXCEPTION: System.TypeLoadException: A type load exception has occurred.
  at Booter.Booter.Main () [0x00010] in /build/src/banshee-2.4.1/src/Clients/Booter/Booter/Entry.cs:82 

The other one gives.....

Unhandled Exception: System.TypeLoadException: A type load exception has occurred.
  at Booter.Booter.Main () [0x00000] in <filename unknown>:0 
[ERROR] FATAL UNHANDLED EXCEPTION: System.TypeLoadException: A type load exception has occurred.
  at Booter.Booter.Main () [0x00000] in <filename unknown>:0

---

### Post by chamber on 2012-06-18
pacman -R mono

pacman -Syyu

pacman -S mono

---

### Post by abnordude on 2012-06-18
> **chamber said:**
> pacman -R mono

pacman -Syyu

pacman -S mono

When i try to remove i get this,

checking dependencies...
error: failed to prepare transaction (could not satisfy dependencies)
:: boo: requires mono
:: dbus-sharp: requires mono
:: gdata-sharp: requires mono
:: gtk-sharp-2: requires mono
:: mono-addins: requires mono>=2.10.5
:: mono-zeroconf: requires mono
:: monodevelop: requires mono>=2.10.5
:: taglib-sharp: requires mono

---

### Post by chamber on 2012-06-18
Just try a reinstall of it then.

---

### Post by abnordude on 2012-06-18
> **chamber said:**
> Just try a reinstall of it then.

Okay,..i'm reinstalling.....

But as there are a few (many) updates....it's taking time.....So, see you a bit later.......

---

### Post by abnordude on 2012-06-28
Sorry for the huge delay......

I tried the sudo pacman syyu mono 

Nope.....Still....am getting the same error.....

---

### Post by chamber on 2012-06-28
Well then, you have truly messed it up.

I would suggest a reinstall and then avoid putting antivirus software on your arch install.

---

### Post by jemadux on 2012-06-28
#pacman -S [gstreamer0.10-ffmpeg]("http://www.archlinux.org/packages/extra/x86_64/gstreamer0.10-ffmpeg/") [gstreamer0.10-good-plugins]("http://www.archlinux.org/packages/extra/x86_64/gstreamer0.10-good-plugins/") [gstreamer0.10-ugly-plugins]("http://www.archlinux.org/packages/extra/x86_64/gstreamer0.10-ugly-plugins/")

---

### Post by abnordude on 2012-07-04
> **jemadux said:**
> #pacman -S [gstreamer0.10-ffmpeg]("http://www.archlinux.org/packages/extra/x86_64/gstreamer0.10-ffmpeg/") [gstreamer0.10-good-plugins]("http://www.archlinux.org/packages/extra/x86_64/gstreamer0.10-good-plugins/") [gstreamer0.10-ugly-plugins]("http://www.archlinux.org/packages/extra/x86_64/gstreamer0.10-ugly-plugins/")

This doesn't help too..

Well....maybe i screwed up the system....

Won't reinstall though...Will adjust with alternative softwares....

Thanks to everyone who have given their best to solve my problem...

---

