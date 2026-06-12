---
title: "Help with amd64 version.."
date: 2006-01-13
forum: Absolute Beginner Talk
---

### Post by madu on 2006-01-13
Hi guys..

I just installed Ubuntu yesterday and am a total noobie..
First I want to clarify a point..
I'm using AMD64 Athlon, and I installed the amd64 version of Ubuntu..
My question is, can I install packages that say something like:
"BLAH-BLAH_i386", or "_i586"...?
Do I have to make them and complile them?
I'm trying to install skype but seems its not working..? 
COund this be the reason?
Alos one more technical question.. I should look around and read beginers guide, yes, but I jusst want skype to get working so that I dont have to go to windows everytime I want to chat with a contact.
The question is:
In Windows, we when we want to install an application, we download it, if its compressed we extract it.
Then we click on a "INSTALL.EXE..SETUP.EXE" file.. 
WHat is the procedure in Linux?
HOw do I identify .EXE files? I know there are no .EXE, but what is the similar one in linux?
What is the general procedure to install.. I see lot of packages are .DEB..
What is the difference between*** apt-get install ***& ***dpkg -i***?
When I say dpkg -i PACK_NAME.deb, does it automatically install?
and guys.. I found this method in the forum to install skype..

 [B][I]install the debian package:

download the debian package for from [http://www.skype.com/go/getskype-linux-deb](http://www.skype.com/go/getskype-linux-deb)
force the installation (we are brave, aren't we?):
sudo dpk -i --force-all ./skype_1.2.0.18-1_i386.deb

install the i386 version of the libqt3-mt library:

download the libqt3-mt package for i386 from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
force the installation (we are brave, aren't we?):
sudo dpk -i --force-all ./libqt3-mt_3.3.4-8ubuntu5_i386.deb

check if skype is missing anything else:
ldd /usr/bin/skype
start skype by typing skype into a console
go, have an old fashioned...[/I][/B]

But it says sudo: dpk: command not found  !!
I dont even have the "make" command..!
WHat do I have t install to get this guys...?

Thanks a lot guys.. SOrry for asking soo many things..!

---

### Post by adwait on 2006-01-13
Uuuh........ok lets start off with the fact that there are no .EXE files in linux. Installation packages in Linux will come with the .deb extension. To install them, you can just double click them and it will ask you for your password.

To install skype, I don't exactly know what to do, but search the forum I am sure it has been discussed.

for the stuff in bold, its not "dpk" its "dpkg" and hence the error.

---

### Post by madu on 2006-01-13
Hi..
YES.. its dpkg.. but still no luck..
but i was foloowing the method in: [http://www.ubuntuforums.org/showthread.php?p=475023#post475023](http://www.ubuntuforums.org/showthread.php?p=475023#post475023)
but get this:
[B][I]maduranga@Maduranga:~/Desktop$ ldd /usr/bin/skype
        linux-gate.so.1 =>  (0xffffe000)
        libqt-mt.so.3 => not found
        libXext.so.6 => /usr/lib32/libXext.so.6 (0x55579000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0x55586000)
        libpthread.so.0 => /lib32/tls/libpthread.so.0 (0x55646000)
        libstdc++.so.5 => /usr/lib32/libstdc++.so.5 (0x55657000)
        libm.so.6 => /lib32/tls/libm.so.6 (0x55711000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0x55733000)
        libc.so.6 => /lib32/tls/libc.so.6 (0x5573f000)
        libdl.so.2 => /lib32/tls/libdl.so.2 (0x5586d000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0x55870000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0x55873000)
        /lib/ld-linux.so.2 (0x55555000)[/I][/B]

what can I do about *libqt-mt.so.3 => not found*
I installed 
 ar -x [B][I]libqt3-mt_3.3.4-8ubuntu5_amd64.deb
[/I][/B] 
but still get that error..
I;m doing things rather blindly.. If someone can guide me.. I would appreciate it very much...

Thank you very much guys..!

---

### Post by Anything Generic on 2006-06-13
I've forced the installation of skype_1.2.0.18-1_i386.deb & libqt3-mt without any luck.  Skype is installed, but won't run.

Now, how do I uninstall these packages?  They installed OK, no errors, but when using dpkg --remove package_name, it says that the package isn't installed.

I just want to revert these changes and try something else... anyone?

---

