---
title: "pcsx"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by nonewmsgs on 2007-11-10
i have tried various psx emulators, and all except this one don't even give me any reponse (sometime i get a bad command or filename even if the executable is in the same directory...) and sometimes i get antoher prompt right below it as if the program has finished without any errors.  pcsx at least gave me a window and i downloaded plugins and some of them it would install (it seems to prefer executables to just libraries...those it just ignores) and i have at least one in every catagory except for cdrom.  i would be perfectly content to use use /media/cdrom0 and have even passed that as a parameter but it did not help.  this really shouldnt be that hard, and ive spent about 5 hours trying to fix this.

this system is running gutsy i386 2.4ghz p4, 1gb ram, geforce 6600 with propritary driver.  all plugins are linux.


william@jesus:~$ pcsx
symlink: /home/william/.pcsx/pcsx.cfg~ -> /home/william/.pcsx/plugins/pcsx.cfg~
symlink: /home/william/.pcsx/pcsx.cfg~ -> /home/william/.pcsx/plugins/cfg/pcsx.cfg~
symlink: /home/william/.pcsx/pcsx.cfg -> /home/william/.pcsx/plugins/pcsx.cfg
symlink: /home/william/.pcsx/pcsx.cfg -> /home/william/.pcsx/plugins/cfg/pcsx.cfg

(<unknown>:3092): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(<unknown>:3092): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed
symlink: /home/william/.pcsx/pcsx.cfg~ -> /home/william/.pcsx/plugins/pcsx.cfg~
symlink: /home/william/.pcsx/pcsx.cfg~ -> /home/william/.pcsx/plugins/cfg/pcsx.cfg~
symlink: /home/william/.pcsx/pcsx.cfg -> /home/william/.pcsx/plugins/pcsx.cfg
symlink: /home/william/.pcsx/pcsx.cfg -> /home/william/.pcsx/plugins/cfg/pcsx.cfg
picking default GPU plugin: 
picking default SPU plugin: 
picking default CD-ROM plugin: 
picking default Controller 1 plugin: 
picking default Controller 2 plugin: 

(<unknown>:3092): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(<unknown>:3092): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed
william@jesus:~$ pscx /media/cdrom0
bash: pscx: command not found
william@jesus:~$ pscx /media/cdrom0
bash: pscx: command not found
william@jesus:~$ pscx 
bash: pscx: command not found
william@jesus:~$ pcsx /media/cdrom0
symlink: /home/william/.pcsx/plugins/cfg/cfg/version_1_8.txt -> /home/william/.pcsx/plugins/version_1_8.txt
symlink: /home/william/.pcsx/plugins/cfg/cfg/version_1_8.txt -> /home/william/.pcsx/plugins/cfg/version_1_8.txt
symlink: /home/william/.pcsx/plugins/cfg/cfg/readme.txt -> /home/william/.pcsx/plugins/readme.txt
symlink: /home/william/.pcsx/plugins/cfg/cfg/readme.txt -> /home/william/.pcsx/plugins/cfg/readme.txt
symlink: /home/william/.pcsx/plugins/cfg/cfg/libcdrmooby-2.8.so -> /home/william/.pcsx/plugins/libcdrmooby-2.8.so
symlink: /home/william/.pcsx/plugins/cfg/cfg/libcdrmooby-2.8.so -> /home/william/.pcsx/plugins/cfg/libcdrmooby-2.8.so
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfg -> /home/william/.pcsx/plugins/cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfg -> /home/william/.pcsx/plugins/cfg/cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/libspuEternal.so.1.41 -> /home/william/.pcsx/plugins/libspuEternal.so.1.41
symlink: /home/william/.pcsx/plugins/cfg/cfg/libspuEternal.so.1.41 -> /home/william/.pcsx/plugins/cfg/libspuEternal.so.1.41
symlink: /home/william/.pcsx/plugins/cfg/cfg/.. -> /home/william/.pcsx/plugins/..
symlink: /home/william/.pcsx/plugins/cfg/cfg/.. -> /home/william/.pcsx/plugins/cfg/..
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfgPeteMesaGL -> /home/william/.pcsx/plugins/cfgPeteMesaGL
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfgPeteMesaGL -> /home/william/.pcsx/plugins/cfg/cfgPeteMesaGL
symlink: /home/william/.pcsx/plugins/cfg/cfg/gpuPeteXGL2.cfg -> /home/william/.pcsx/plugins/gpuPeteXGL2.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/gpuPeteXGL2.cfg -> /home/william/.pcsx/plugins/cfg/gpuPeteXGL2.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/omnijoy-1.0.0-beta2 -> /home/william/.pcsx/plugins/omnijoy-1.0.0-beta2
symlink: /home/william/.pcsx/plugins/cfg/cfg/omnijoy-1.0.0-beta2 -> /home/william/.pcsx/plugins/cfg/omnijoy-1.0.0-beta2
symlink: /home/william/.pcsx/plugins/cfg/cfg/pcsx.cfg~ -> /home/william/.pcsx/plugins/pcsx.cfg~
symlink: /home/william/.pcsx/plugins/cfg/cfg/pcsx.cfg~ -> /home/william/.pcsx/plugins/cfg/pcsx.cfg~
symlink: /home/william/.pcsx/plugins/cfg/cfg/gpuPeteMesaGL.cfg -> /home/william/.pcsx/plugins/gpuPeteMesaGL.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/gpuPeteMesaGL.cfg -> /home/william/.pcsx/plugins/cfg/gpuPeteMesaGL.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfgPadJoy -> /home/william/.pcsx/plugins/cfgPadJoy
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfgPadJoy -> /home/william/.pcsx/plugins/cfg/cfgPadJoy
symlink: /home/william/.pcsx/plugins/cfg/cfg/pcsx.cfg -> /home/william/.pcsx/plugins/pcsx.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/pcsx.cfg -> /home/william/.pcsx/plugins/cfg/pcsx.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/. -> /home/william/.pcsx/plugins/.
symlink: /home/william/.pcsx/plugins/cfg/cfg/. -> /home/william/.pcsx/plugins/cfg/.
symlink: /home/william/.pcsx/plugins/cfg/cfg/version.txt -> /home/william/.pcsx/plugins/version.txt
symlink: /home/william/.pcsx/plugins/cfg/cfg/version.txt -> /home/william/.pcsx/plugins/cfg/version.txt
symlink: /home/william/.pcsx/plugins/cfg/cfg/libspuPeopsOSS.so.1.0.8 -> /home/william/.pcsx/plugins/libspuPeopsOSS.so.1.0.8
symlink: /home/william/.pcsx/plugins/cfg/cfg/libspuPeopsOSS.so.1.0.8 -> /home/william/.pcsx/plugins/cfg/libspuPeopsOSS.so.1.0.8
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfgPeopsOSS -> /home/william/.pcsx/plugins/cfgPeopsOSS
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfgPeopsOSS -> /home/william/.pcsx/plugins/cfg/cfgPeopsOSS
symlink: /home/william/.pcsx/plugins/cfg/cfg/spuPeopsOSS.cfg -> /home/william/.pcsx/plugins/spuPeopsOSS.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/spuPeopsOSS.cfg -> /home/william/.pcsx/plugins/cfg/spuPeopsOSS.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/readme_1_8.txt -> /home/william/.pcsx/plugins/readme_1_8.txt
symlink: /home/william/.pcsx/plugins/cfg/cfg/readme_1_8.txt -> /home/william/.pcsx/plugins/cfg/readme_1_8.txt
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfgPeteXGL2 -> /home/william/.pcsx/plugins/cfgPeteXGL2
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfgPeteXGL2 -> /home/william/.pcsx/plugins/cfg/cfgPeteXGL2
symlink: /home/william/.pcsx/plugins/cfg/cfg/padJoy.cfg -> /home/william/.pcsx/plugins/padJoy.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/padJoy.cfg -> /home/william/.pcsx/plugins/cfg/padJoy.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/libgpuPeteMesaGL.so.1.0.76 -> /home/william/.pcsx/plugins/libgpuPeteMesaGL.so.1.0.76
symlink: /home/william/.pcsx/plugins/cfg/cfg/libgpuPeteMesaGL.so.1.0.76 -> /home/william/.pcsx/plugins/cfg/libgpuPeteMesaGL.so.1.0.76
symlink: /home/william/.pcsx/plugins/cfg/cfg/libgpuPeteXGL2.so.2.0.8 -> /home/william/.pcsx/plugins/libgpuPeteXGL2.so.2.0.8
symlink: /home/william/.pcsx/plugins/cfg/cfg/libgpuPeteXGL2.so.2.0.8 -> /home/william/.pcsx/plugins/cfg/libgpuPeteXGL2.so.2.0.8
/home/william/.pcsx/plugins/libcdrmooby-2.8.so: undefined symbol: XftDrawSetClip
libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

(<unknown>:4533): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(<unknown>:4533): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed
/home/william/.pcsx/plugins/libcdrmooby-2.8.so: undefined symbol: XftDrawSetClip
libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

(<unknown>:4533): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(<unknown>:4533): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed
symlink: /home/william/.pcsx/plugins/cfg/cfg/version_1_8.txt -> /home/william/.pcsx/plugins/version_1_8.txt
symlink: /home/william/.pcsx/plugins/cfg/cfg/version_1_8.txt -> /home/william/.pcsx/plugins/cfg/version_1_8.txt
symlink: /home/william/.pcsx/plugins/cfg/cfg/readme.txt -> /home/william/.pcsx/plugins/readme.txt
symlink: /home/william/.pcsx/plugins/cfg/cfg/readme.txt -> /home/william/.pcsx/plugins/cfg/readme.txt
symlink: /home/william/.pcsx/plugins/cfg/cfg/libcdrmooby-2.8.so -> /home/william/.pcsx/plugins/libcdrmooby-2.8.so
symlink: /home/william/.pcsx/plugins/cfg/cfg/libcdrmooby-2.8.so -> /home/william/.pcsx/plugins/cfg/libcdrmooby-2.8.so
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfg -> /home/william/.pcsx/plugins/cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfg -> /home/william/.pcsx/plugins/cfg/cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/libspuEternal.so.1.41 -> /home/william/.pcsx/plugins/libspuEternal.so.1.41
symlink: /home/william/.pcsx/plugins/cfg/cfg/libspuEternal.so.1.41 -> /home/william/.pcsx/plugins/cfg/libspuEternal.so.1.41
symlink: /home/william/.pcsx/plugins/cfg/cfg/.. -> /home/william/.pcsx/plugins/..
symlink: /home/william/.pcsx/plugins/cfg/cfg/.. -> /home/william/.pcsx/plugins/cfg/..
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfgPeteMesaGL -> /home/william/.pcsx/plugins/cfgPeteMesaGL
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfgPeteMesaGL -> /home/william/.pcsx/plugins/cfg/cfgPeteMesaGL
symlink: /home/william/.pcsx/plugins/cfg/cfg/gpuPeteXGL2.cfg -> /home/william/.pcsx/plugins/gpuPeteXGL2.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/gpuPeteXGL2.cfg -> /home/william/.pcsx/plugins/cfg/gpuPeteXGL2.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/omnijoy-1.0.0-beta2 -> /home/william/.pcsx/plugins/omnijoy-1.0.0-beta2
symlink: /home/william/.pcsx/plugins/cfg/cfg/omnijoy-1.0.0-beta2 -> /home/william/.pcsx/plugins/cfg/omnijoy-1.0.0-beta2
symlink: /home/william/.pcsx/plugins/cfg/cfg/pcsx.cfg~ -> /home/william/.pcsx/plugins/pcsx.cfg~
symlink: /home/william/.pcsx/plugins/cfg/cfg/pcsx.cfg~ -> /home/william/.pcsx/plugins/cfg/pcsx.cfg~
symlink: /home/william/.pcsx/plugins/cfg/cfg/gpuPeteMesaGL.cfg -> /home/william/.pcsx/plugins/gpuPeteMesaGL.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/gpuPeteMesaGL.cfg -> /home/william/.pcsx/plugins/cfg/gpuPeteMesaGL.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfgPadJoy -> /home/william/.pcsx/plugins/cfgPadJoy
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfgPadJoy -> /home/william/.pcsx/plugins/cfg/cfgPadJoy
symlink: /home/william/.pcsx/plugins/cfg/cfg/pcsx.cfg -> /home/william/.pcsx/plugins/pcsx.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/pcsx.cfg -> /home/william/.pcsx/plugins/cfg/pcsx.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/. -> /home/william/.pcsx/plugins/.
symlink: /home/william/.pcsx/plugins/cfg/cfg/. -> /home/william/.pcsx/plugins/cfg/.
symlink: /home/william/.pcsx/plugins/cfg/cfg/version.txt -> /home/william/.pcsx/plugins/version.txt
symlink: /home/william/.pcsx/plugins/cfg/cfg/version.txt -> /home/william/.pcsx/plugins/cfg/version.txt
symlink: /home/william/.pcsx/plugins/cfg/cfg/libspuPeopsOSS.so.1.0.8 -> /home/william/.pcsx/plugins/libspuPeopsOSS.so.1.0.8
symlink: /home/william/.pcsx/plugins/cfg/cfg/libspuPeopsOSS.so.1.0.8 -> /home/william/.pcsx/plugins/cfg/libspuPeopsOSS.so.1.0.8
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfgPeopsOSS -> /home/william/.pcsx/plugins/cfgPeopsOSS
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfgPeopsOSS -> /home/william/.pcsx/plugins/cfg/cfgPeopsOSS
symlink: /home/william/.pcsx/plugins/cfg/cfg/spuPeopsOSS.cfg -> /home/william/.pcsx/plugins/spuPeopsOSS.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/spuPeopsOSS.cfg -> /home/william/.pcsx/plugins/cfg/spuPeopsOSS.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/readme_1_8.txt -> /home/william/.pcsx/plugins/readme_1_8.txt
symlink: /home/william/.pcsx/plugins/cfg/cfg/readme_1_8.txt -> /home/william/.pcsx/plugins/cfg/readme_1_8.txt
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfgPeteXGL2 -> /home/william/.pcsx/plugins/cfgPeteXGL2
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfgPeteXGL2 -> /home/william/.pcsx/plugins/cfg/cfgPeteXGL2
symlink: /home/william/.pcsx/plugins/cfg/cfg/padJoy.cfg -> /home/william/.pcsx/plugins/padJoy.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/padJoy.cfg -> /home/william/.pcsx/plugins/cfg/padJoy.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/libgpuPeteMesaGL.so.1.0.76 -> /home/william/.pcsx/plugins/libgpuPeteMesaGL.so.1.0.76
symlink: /home/william/.pcsx/plugins/cfg/cfg/libgpuPeteMesaGL.so.1.0.76 -> /home/william/.pcsx/plugins/cfg/libgpuPeteMesaGL.so.1.0.76
symlink: /home/william/.pcsx/plugins/cfg/cfg/libgpuPeteXGL2.so.2.0.8 -> /home/william/.pcsx/plugins/libgpuPeteXGL2.so.2.0.8
symlink: /home/william/.pcsx/plugins/cfg/cfg/libgpuPeteXGL2.so.2.0.8 -> /home/william/.pcsx/plugins/cfg/libgpuPeteXGL2.so.2.0.8
/home/william/.pcsx/plugins/libcdrmooby-2.8.so: undefined symbol: XftDrawSetClip
libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
picking default CD-ROM plugin: 

(<unknown>:4533): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(<unknown>:4533): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed
symlink: /home/william/.pcsx/plugins/cfg/cfg/version_1_8.txt -> /home/william/.pcsx/plugins/version_1_8.txt
symlink: /home/william/.pcsx/plugins/cfg/cfg/version_1_8.txt -> /home/william/.pcsx/plugins/cfg/version_1_8.txt
symlink: /home/william/.pcsx/plugins/cfg/cfg/readme.txt -> /home/william/.pcsx/plugins/readme.txt
symlink: /home/william/.pcsx/plugins/cfg/cfg/readme.txt -> /home/william/.pcsx/plugins/cfg/readme.txt
symlink: /home/william/.pcsx/plugins/cfg/cfg/libcdrmooby-2.8.so -> /home/william/.pcsx/plugins/libcdrmooby-2.8.so
symlink: /home/william/.pcsx/plugins/cfg/cfg/libcdrmooby-2.8.so -> /home/william/.pcsx/plugins/cfg/libcdrmooby-2.8.so
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfg -> /home/william/.pcsx/plugins/cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfg -> /home/william/.pcsx/plugins/cfg/cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/libspuEternal.so.1.41 -> /home/william/.pcsx/plugins/libspuEternal.so.1.41
symlink: /home/william/.pcsx/plugins/cfg/cfg/libspuEternal.so.1.41 -> /home/william/.pcsx/plugins/cfg/libspuEternal.so.1.41
symlink: /home/william/.pcsx/plugins/cfg/cfg/.. -> /home/william/.pcsx/plugins/..
symlink: /home/william/.pcsx/plugins/cfg/cfg/.. -> /home/william/.pcsx/plugins/cfg/..
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfgPeteMesaGL -> /home/william/.pcsx/plugins/cfgPeteMesaGL
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfgPeteMesaGL -> /home/william/.pcsx/plugins/cfg/cfgPeteMesaGL
symlink: /home/william/.pcsx/plugins/cfg/cfg/gpuPeteXGL2.cfg -> /home/william/.pcsx/plugins/gpuPeteXGL2.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/gpuPeteXGL2.cfg -> /home/william/.pcsx/plugins/cfg/gpuPeteXGL2.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/omnijoy-1.0.0-beta2 -> /home/william/.pcsx/plugins/omnijoy-1.0.0-beta2
symlink: /home/william/.pcsx/plugins/cfg/cfg/omnijoy-1.0.0-beta2 -> /home/william/.pcsx/plugins/cfg/omnijoy-1.0.0-beta2
symlink: /home/william/.pcsx/plugins/cfg/cfg/pcsx.cfg~ -> /home/william/.pcsx/plugins/pcsx.cfg~
symlink: /home/william/.pcsx/plugins/cfg/cfg/pcsx.cfg~ -> /home/william/.pcsx/plugins/cfg/pcsx.cfg~
symlink: /home/william/.pcsx/plugins/cfg/cfg/gpuPeteMesaGL.cfg -> /home/william/.pcsx/plugins/gpuPeteMesaGL.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/gpuPeteMesaGL.cfg -> /home/william/.pcsx/plugins/cfg/gpuPeteMesaGL.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfgPadJoy -> /home/william/.pcsx/plugins/cfgPadJoy
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfgPadJoy -> /home/william/.pcsx/plugins/cfg/cfgPadJoy
symlink: /home/william/.pcsx/plugins/cfg/cfg/pcsx.cfg -> /home/william/.pcsx/plugins/pcsx.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/pcsx.cfg -> /home/william/.pcsx/plugins/cfg/pcsx.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/. -> /home/william/.pcsx/plugins/.
symlink: /home/william/.pcsx/plugins/cfg/cfg/. -> /home/william/.pcsx/plugins/cfg/.
symlink: /home/william/.pcsx/plugins/cfg/cfg/version.txt -> /home/william/.pcsx/plugins/version.txt
symlink: /home/william/.pcsx/plugins/cfg/cfg/version.txt -> /home/william/.pcsx/plugins/cfg/version.txt
symlink: /home/william/.pcsx/plugins/cfg/cfg/libspuPeopsOSS.so.1.0.8 -> /home/william/.pcsx/plugins/libspuPeopsOSS.so.1.0.8
symlink: /home/william/.pcsx/plugins/cfg/cfg/libspuPeopsOSS.so.1.0.8 -> /home/william/.pcsx/plugins/cfg/libspuPeopsOSS.so.1.0.8
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfgPeopsOSS -> /home/william/.pcsx/plugins/cfgPeopsOSS
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfgPeopsOSS -> /home/william/.pcsx/plugins/cfg/cfgPeopsOSS
symlink: /home/william/.pcsx/plugins/cfg/cfg/spuPeopsOSS.cfg -> /home/william/.pcsx/plugins/spuPeopsOSS.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/spuPeopsOSS.cfg -> /home/william/.pcsx/plugins/cfg/spuPeopsOSS.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/readme_1_8.txt -> /home/william/.pcsx/plugins/readme_1_8.txt
symlink: /home/william/.pcsx/plugins/cfg/cfg/readme_1_8.txt -> /home/william/.pcsx/plugins/cfg/readme_1_8.txt
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfgPeteXGL2 -> /home/william/.pcsx/plugins/cfgPeteXGL2
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfgPeteXGL2 -> /home/william/.pcsx/plugins/cfg/cfgPeteXGL2
symlink: /home/william/.pcsx/plugins/cfg/cfg/padJoy.cfg -> /home/william/.pcsx/plugins/padJoy.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/padJoy.cfg -> /home/william/.pcsx/plugins/cfg/padJoy.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/libgpuPeteMesaGL.so.1.0.76 -> /home/william/.pcsx/plugins/libgpuPeteMesaGL.so.1.0.76
symlink: /home/william/.pcsx/plugins/cfg/cfg/libgpuPeteMesaGL.so.1.0.76 -> /home/william/.pcsx/plugins/cfg/libgpuPeteMesaGL.so.1.0.76
symlink: /home/william/.pcsx/plugins/cfg/cfg/libgpuPeteXGL2.so.2.0.8 -> /home/william/.pcsx/plugins/libgpuPeteXGL2.so.2.0.8
symlink: /home/william/.pcsx/plugins/cfg/cfg/libgpuPeteXGL2.so.2.0.8 -> /home/william/.pcsx/plugins/cfg/libgpuPeteXGL2.so.2.0.8
/home/william/.pcsx/plugins/libcdrmooby-2.8.so: undefined symbol: XftDrawSetClip
libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

(<unknown>:4533): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(<unknown>:4533): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed
/home/william/.pcsx/plugins/libcdrmooby-2.8.so: undefined symbol: XftDrawSetClip
libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

(<unknown>:4533): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(<unknown>:4533): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed
symlink: /home/william/.pcsx/plugins/cfg/cfg/version_1_8.txt -> /home/william/.pcsx/plugins/version_1_8.txt
symlink: /home/william/.pcsx/plugins/cfg/cfg/version_1_8.txt -> /home/william/.pcsx/plugins/cfg/version_1_8.txt
symlink: /home/william/.pcsx/plugins/cfg/cfg/readme.txt -> /home/william/.pcsx/plugins/readme.txt
symlink: /home/william/.pcsx/plugins/cfg/cfg/readme.txt -> /home/william/.pcsx/plugins/cfg/readme.txt
symlink: /home/william/.pcsx/plugins/cfg/cfg/libcdrmooby-2.8.so -> /home/william/.pcsx/plugins/libcdrmooby-2.8.so
symlink: /home/william/.pcsx/plugins/cfg/cfg/libcdrmooby-2.8.so -> /home/william/.pcsx/plugins/cfg/libcdrmooby-2.8.so
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfg -> /home/william/.pcsx/plugins/cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfg -> /home/william/.pcsx/plugins/cfg/cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/libspuEternal.so.1.41 -> /home/william/.pcsx/plugins/libspuEternal.so.1.41
symlink: /home/william/.pcsx/plugins/cfg/cfg/libspuEternal.so.1.41 -> /home/william/.pcsx/plugins/cfg/libspuEternal.so.1.41
symlink: /home/william/.pcsx/plugins/cfg/cfg/.. -> /home/william/.pcsx/plugins/..
symlink: /home/william/.pcsx/plugins/cfg/cfg/.. -> /home/william/.pcsx/plugins/cfg/..
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfgPeteMesaGL -> /home/william/.pcsx/plugins/cfgPeteMesaGL
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfgPeteMesaGL -> /home/william/.pcsx/plugins/cfg/cfgPeteMesaGL
symlink: /home/william/.pcsx/plugins/cfg/cfg/gpuPeteXGL2.cfg -> /home/william/.pcsx/plugins/gpuPeteXGL2.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/gpuPeteXGL2.cfg -> /home/william/.pcsx/plugins/cfg/gpuPeteXGL2.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/omnijoy-1.0.0-beta2 -> /home/william/.pcsx/plugins/omnijoy-1.0.0-beta2
symlink: /home/william/.pcsx/plugins/cfg/cfg/omnijoy-1.0.0-beta2 -> /home/william/.pcsx/plugins/cfg/omnijoy-1.0.0-beta2
symlink: /home/william/.pcsx/plugins/cfg/cfg/pcsx.cfg~ -> /home/william/.pcsx/plugins/pcsx.cfg~
symlink: /home/william/.pcsx/plugins/cfg/cfg/pcsx.cfg~ -> /home/william/.pcsx/plugins/cfg/pcsx.cfg~
symlink: /home/william/.pcsx/plugins/cfg/cfg/gpuPeteMesaGL.cfg -> /home/william/.pcsx/plugins/gpuPeteMesaGL.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/gpuPeteMesaGL.cfg -> /home/william/.pcsx/plugins/cfg/gpuPeteMesaGL.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfgPadJoy -> /home/william/.pcsx/plugins/cfgPadJoy
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfgPadJoy -> /home/william/.pcsx/plugins/cfg/cfgPadJoy
symlink: /home/william/.pcsx/plugins/cfg/cfg/pcsx.cfg -> /home/william/.pcsx/plugins/pcsx.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/pcsx.cfg -> /home/william/.pcsx/plugins/cfg/pcsx.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/. -> /home/william/.pcsx/plugins/.
symlink: /home/william/.pcsx/plugins/cfg/cfg/. -> /home/william/.pcsx/plugins/cfg/.
symlink: /home/william/.pcsx/plugins/cfg/cfg/version.txt -> /home/william/.pcsx/plugins/version.txt
symlink: /home/william/.pcsx/plugins/cfg/cfg/version.txt -> /home/william/.pcsx/plugins/cfg/version.txt
symlink: /home/william/.pcsx/plugins/cfg/cfg/libspuPeopsOSS.so.1.0.8 -> /home/william/.pcsx/plugins/libspuPeopsOSS.so.1.0.8
symlink: /home/william/.pcsx/plugins/cfg/cfg/libspuPeopsOSS.so.1.0.8 -> /home/william/.pcsx/plugins/cfg/libspuPeopsOSS.so.1.0.8
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfgPeopsOSS -> /home/william/.pcsx/plugins/cfgPeopsOSS
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfgPeopsOSS -> /home/william/.pcsx/plugins/cfg/cfgPeopsOSS
symlink: /home/william/.pcsx/plugins/cfg/cfg/spuPeopsOSS.cfg -> /home/william/.pcsx/plugins/spuPeopsOSS.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/spuPeopsOSS.cfg -> /home/william/.pcsx/plugins/cfg/spuPeopsOSS.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/readme_1_8.txt -> /home/william/.pcsx/plugins/readme_1_8.txt
symlink: /home/william/.pcsx/plugins/cfg/cfg/readme_1_8.txt -> /home/william/.pcsx/plugins/cfg/readme_1_8.txt
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfgPeteXGL2 -> /home/william/.pcsx/plugins/cfgPeteXGL2
symlink: /home/william/.pcsx/plugins/cfg/cfg/cfgPeteXGL2 -> /home/william/.pcsx/plugins/cfg/cfgPeteXGL2
symlink: /home/william/.pcsx/plugins/cfg/cfg/padJoy.cfg -> /home/william/.pcsx/plugins/padJoy.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/padJoy.cfg -> /home/william/.pcsx/plugins/cfg/padJoy.cfg
symlink: /home/william/.pcsx/plugins/cfg/cfg/libgpuPeteMesaGL.so.1.0.76 -> /home/william/.pcsx/plugins/libgpuPeteMesaGL.so.1.0.76
symlink: /home/william/.pcsx/plugins/cfg/cfg/libgpuPeteMesaGL.so.1.0.76 -> /home/william/.pcsx/plugins/cfg/libgpuPeteMesaGL.so.1.0.76
symlink: /home/william/.pcsx/plugins/cfg/cfg/libgpuPeteXGL2.so.2.0.8 -> /home/william/.pcsx/plugins/libgpuPeteXGL2.so.2.0.8
symlink: /home/william/.pcsx/plugins/cfg/cfg/libgpuPeteXGL2.so.2.0.8 -> /home/william/.pcsx/plugins/cfg/libgpuPeteXGL2.so.2.0.8
/home/william/.pcsx/plugins/libcdrmooby-2.8.so: undefined symbol: XftDrawSetClip
libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
picking default CD-ROM plugin: 

(<unknown>:4533): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(<unknown>:4533): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

---

