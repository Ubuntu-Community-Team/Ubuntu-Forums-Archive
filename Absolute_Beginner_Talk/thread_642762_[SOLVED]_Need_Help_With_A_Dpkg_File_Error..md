---
title: "[SOLVED] Need Help With A Dpkg File Error."
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by toofast on 2007-12-16
Thanks everyone for your time helping me solve this problem.  Works perfect now and my computer takes its updates. :guitar: Rock on

---

### Post by toofast on 2007-12-16
bump

---

### Post by AndyCooll on 2007-12-16
When creating a title for your thread "Help" actually isn't very helpful since everyone on these forums is seeking help, You are more likely to get responses if your title is more specific, e.g. in this case "updates error message" or something similar. When browsing this board most folk simply ignore non-descriptive titles.

Judging from the error message you stopped an installation of something before it had completed. To fix this try opening a terminal (Applications > Accessories > Terminal) and in it typing the following:
```
sudo dpkg --configure -a
```
After that try installing the app you were trying to install again.

:cool:

---

### Post by toofast on 2007-12-16
Advice taking,  thank you for your help.  I'm new to this so not to familier where to find the applications you speak of. Sorry you have to hate newbies could you steer me in the right direction. Thanks again

---

### Post by toofast on 2007-12-16
When I click on applications then click on accessories and then terminal, it comes up a box for me to type in so I copied and pasted what you said to put in then it asks for a password when I try to put in my password it doesn't accept it is there a different way.:confused:

---

### Post by t-bone510 on 2007-12-16
you know its not supposed to show your password when you type it... just type it like you normally would and hit enter

---

### Post by toofast on 2007-12-16
I entered the password know it just pops up the same thing I pasted instead of incorrect password. also when I open the terminal it comes up with bryan@dale-desktop:~$  bryan is my name but is it supposed to say that or no? If not what do I do to make it so it comes up blank because when I try to delete what comes up automaticaly it makes a crazy noise and will not delete.:confused:

---

### Post by toofast on 2007-12-16
when I try to type in the password it doesn't:confused: even show black dot's or anything the blinkingline where the letters should go isnt even there.

---

### Post by AndyCooll on 2007-12-16
You are welcome. I assumed you were new, hence the reason I gave you the path for each application.

In the case of the command line, it sounds like you are doing the correct thing. The password should be your login password (assuming that when you installed Ubuntu yours was the first account you created) and when you need admin rights that is the password you've always used so far.

In effect the command "sudo" merely says give me admin privileges for the following action, i.e. the rest of the sentence. Hence being asked for your password.

You haven't accidentally got caps lock on or something like that have you?

Perhaps I can suggest you try again.

:cool:

---

### Post by t-bone510 on 2007-12-16
When you type the password, NOTHING IS SUPPOSED TO APPEAR

Just type it as you normally would and hit enter.... 

:x

---

### Post by t-bone510 on 2007-12-16
wait.. it says 

bryan@dale-desktop

That means he is a second user and the person "Dale" may have disabled sudo for his account

---

### Post by AndyCooll on 2007-12-16
> **toofast said:**
> I entered the password know it just pops up the same thing I pasted instead of incorrect password. also when I open the terminal it comes up with bryan@dale-desktop:~$  bryan is my name but is it supposed to say that or no? If not what do I do to make it so it comes up blank because when I try to delete what comes up automaticaly it makes a crazy noise and will not delete.:confused:

Yes that is correct. It is merely showing you that you are in your home directory (it's the command line equivalent of what you might see in a gui).

:cool:

---

### Post by toofast on 2007-12-16
should it be typed it like this .......    sudo dpkg --configure -a    or like this   sudodpkg--configure-a

I am not sure but now it isn't asking me for a password.

---

### Post by AndyCooll on 2007-12-16
> **t-bone510 said:**
> wait.. it says 

bryan@dale-desktop

That means he is a second user and the person "Dale" may have disabled sudo for his account

Ahhh ...yes missed that point.

How was your OS installed? Has someone installed it for you?

:cool:

---

### Post by AndyCooll on 2007-12-16
> **toofast said:**
> should it be typed it like this .......    sudo dpkg --configure -a    or like this   sudodpkg--configure-a

I am not sure but now it isn't asking me for a password.

The command I gave you is correct (including the spaces).

:cool:

---

### Post by toofast on 2007-12-16
Ths is what it says when I put in the sudo.


Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
dale@dale-desktop:~$ dpkg --help
Usage: dpkg [<option> ...] <command>

Commands:
  -i|--install       <.deb file name> ... | -R|--recursive <directory> ...
  --unpack           <.deb file name> ... | -R|--recursive <directory> ...
  -A|--record-avail  <.deb file name> ... | -R|--recursive <directory> ...
  --configure        <package> ... | -a|--pending
  -r|--remove        <package> ... | -a|--pending
  -P|--purge         <package> ... | -a|--pending
  --get-selections [<pattern> ...] Get list of selections to stdout.
  --set-selections                 Set package selections from stdin.
  --clear-selections               Deselect every non-essential package.
  --update-avail <Packages-file>   Replace available packages info.
  --merge-avail <Packages-file>    Merge with info from file.
  --clear-avail                    Erase existing available info.
  --forget-old-unavail             Forget uninstalled unavailable pkgs.
  -s|--status <package> ...        Display package status details.
  -p|--print-avail <package> ...   Display available version details.
  -L|--listfiles <package> ...     List files `owned' by package(s).
  -l|--list [<pattern> ...]        List packages concisely.
  -S|--search <pattern> ...        Find package(s) owning file(s).
  -C|--audit                       Check for broken package(s).
  --print-architecture             Print dpkg architecture.
  --compare-versions <a> <op> <b>  Compare version numbers - see below.
  --force-help                     Show help on forcing.
  -Dh|--debug=help                 Show help on debugging.

  -h|--help                        Show this help message.
  --version                        Show the version.
  --license|--licence              Show the copyright licensing terms.

Use dpkg -b|--build|-c|--contents|-e|--control|-I|--info|-f|--field|
 -x|--extract|-X|--vextract|--fsys-tarfile  on archives (type dpkg-deb --help).

For internal use: dpkg --assert-support-predepends | --predep-package |
  --assert-working-epoch | --assert-long-filenames | --assert-multi-conrep.

Options:
  --admindir=<directory>     Use <directory> instead of /var/lib/dpkg.
  --root=<directory>         Install on a different root directory.
  --instdir=<directory>      Change installation dir without changing admin dir.
  -O|--selected-only         Skip packages not selected for install/upgrade.
  -E|--skip-same-version     Skip packages whose same version is installed.
  -G|--refuse-downgrade      Skip packages with earlier version than installed.
  -B|--auto-deconfigure      Install even if it would break some other package.
  --no-debsig                Do not try to verify package signatures.
  --no-act|--dry-run|--simulate
                             Just say what we would do - don't do it.
  -D|--debug=<octal>         Enable debugging (see -Dhelp or --debug=help).
  --status-fd <n>            Send status change updates to file descriptor <n>.
  --log=<filename>           Log status changes and actions to <filename>.
  --ignore-depends=<package>,...
                             Ignore dependencies involving <package>.
  --force-...                Override problems (see --force-help).
  --no-force-...|--refuse-...
                             Stop when problems encountered.
  --abort-after <n>          Abort after encountering <n> errors.

Comparison operators for --compare-versions are:
  lt le eq ne ge gt       (treat empty version as earlier than any version);
  lt-nl le-nl ge-nl gt-nl (treat empty version as later than any version);
  < << <= = >= >> >       (only for compatibility with control file syntax).

Use `dselect' or `aptitude' for user-friendly package management.
dale@dale-desktop:~$ 466466
bash: 466466: command not found
dale@dale-desktop:~$ --unpack
Usage: command-not-found [options] <command-name>

command-not-found: error: no such option: --unpack
bash: --unpack: command not found
dale@dale-desktop:~$  -i|--unpack
Usage: command-not-found [options] <command-name>

command-not-found: error: no such option: --unpack
bash: --unpack: command not found
Usage: command-not-found [options] <command-name>

command-not-found: error: no such option: -i
bash: -i: command not found
dale@dale-desktop:~$

---

### Post by toofast on 2007-12-16
still need help bump to the top.

---

### Post by MONODA on 2007-12-16
I remember getting this error as well when I first started using ubuntu. This happens when you cancel an installation in the middle of it. There is an easy solution which I cant remember. I would search on the forums, google and [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu) for the solution.

---

### Post by toofast on 2007-12-17
Still need help on getting this problem fixed. I now know that I tried installing virtual box and cancelled somehow and that is the problem. But how do I fix this problem. I went to the terminal and put in the sudo code and it didnt work please someone help me that can walk me through this process. thank you very much.

---

### Post by toofast on 2007-12-17
Ok I am trying to make it so I can update my computer. I am running feisty fawn because I cannot download gusty. The reason I cannot download gutsy is because I have a DPKG problem. I tried to download the virtual box and something happened during the download and now when I try to download anything it says error dpkg. When I try to put in the sudo code it doesn't work. So please either in this thread or the other I need help thank you very much.

---

### Post by toofast on 2007-12-17
bump:confused:

---

### Post by toofast on 2007-12-17
I oped a terminal and put the sudo code in and it didn't work it popped up a bunch of crazy stuff but the guy who told me to do it said it should have shown up something else then stopped helping me so I was left in the dark.

So if any one would like to help me it would be very appreciated.

---

### Post by jken146 on 2007-12-17
Please give more details, like what you were trying to do, the exact commands you used and the errors you got.

---

### Post by toofast on 2007-12-17
I will post it all for you give me one second

---

### Post by toofast on 2007-12-17
dale@dale-desktop:~$ sudo dpkg --configure -a
dale@dale-desktop:~$ sudo dpkg --configure -a
dale@dale-desktop:~$ sudo dpkg --configure -a466466
dpkg: unknown option -4

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
dale@dale-desktop:~$ dpkg --help
Usage: dpkg [<option> ...] <command>

Commands:
  -i|--install       <.deb file name> ... | -R|--recursive <directory> ...
  --unpack           <.deb file name> ... | -R|--recursive <directory> ...
  -A|--record-avail  <.deb file name> ... | -R|--recursive <directory> ...
  --configure        <package> ... | -a|--pending
  -r|--remove        <package> ... | -a|--pending
  -P|--purge         <package> ... | -a|--pending
  --get-selections [<pattern> ...] Get list of selections to stdout.
  --set-selections                 Set package selections from stdin.
  --clear-selections               Deselect every non-essential package.
  --update-avail <Packages-file>   Replace available packages info.
  --merge-avail <Packages-file>    Merge with info from file.
  --clear-avail                    Erase existing available info.
  --forget-old-unavail             Forget uninstalled unavailable pkgs.
  -s|--status <package> ...        Display package status details.
  -p|--print-avail <package> ...   Display available version details.
  -L|--listfiles <package> ...     List files `owned' by package(s).
  -l|--list [<pattern> ...]        List packages concisely.
  -S|--search <pattern> ...        Find package(s) owning file(s).
  -C|--audit                       Check for broken package(s).
  --print-architecture             Print dpkg architecture.
  --compare-versions <a> <op> <b>  Compare version numbers - see below.
  --force-help                     Show help on forcing.
  -Dh|--debug=help                 Show help on debugging.

  -h|--help                        Show this help message.
  --version                        Show the version.
  --license|--licence              Show the copyright licensing terms.

Use dpkg -b|--build|-c|--contents|-e|--control|-I|--info|-f|--field|
 -x|--extract|-X|--vextract|--fsys-tarfile  on archives (type dpkg-deb --help).

For internal use: dpkg --assert-support-predepends | --predep-package |
  --assert-working-epoch | --assert-long-filenames | --assert-multi-conrep.

Options:
  --admindir=<directory>     Use <directory> instead of /var/lib/dpkg.
  --root=<directory>         Install on a different root directory.
  --instdir=<directory>      Change installation dir without changing admin dir.
  -O|--selected-only         Skip packages not selected for install/upgrade.
  -E|--skip-same-version     Skip packages whose same version is installed.
  -G|--refuse-downgrade      Skip packages with earlier version than installed.
  -B|--auto-deconfigure      Install even if it would break some other package.
  --no-debsig                Do not try to verify package signatures.
  --no-act|--dry-run|--simulate
                             Just say what we would do - don't do it.
  -D|--debug=<octal>         Enable debugging (see -Dhelp or --debug=help).
  --status-fd <n>            Send status change updates to file descriptor <n>.
  --log=<filename>           Log status changes and actions to <filename>.
  --ignore-depends=<package>,...
                             Ignore dependencies involving <package>.
  --force-...                Override problems (see --force-help).
  --no-force-...|--refuse-...
                             Stop when problems encountered.
  --abort-after <n>          Abort after encountering <n> errors.

Comparison operators for --compare-versions are:
  lt le eq ne ge gt       (treat empty version as earlier than any version);
  lt-nl le-nl ge-nl gt-nl (treat empty version as later than any version);
  < << <= = >= >> >       (only for compatibility with control file syntax).

Use `dselect' or `aptitude' for user-friendly package management.
dale@dale-desktop:~$ 

I am not sure if the answer I am looking for is in here or not but maybe you can figure it out.

---

### Post by toofast on 2007-12-17
When I try to update it says this.


Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package virtualbox needs to be reinstalled, but I can't find an archive for it.'

---

### Post by toofast on 2007-12-17
I see no one here can help that really sucks I thought these forums were for help??????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????

---

### Post by strabes on 2007-12-17
You need to be more specific. People can't see your screen nor read your mind. I apologize that no one has replied yet. Please paste the output of this command:```
sudo aptitude update && sudo aptitude clean && sudo aptitude dist-upgrade
```

---

### Post by jocko on 2007-12-17
1. Explain your problem properly. How do you expect people to be able to help you if you don't explain the problem?
2. Take it easy. I see you have multiple post with what I guess is the same problem.

Edit: Good. I see someone saw the multiple threads and joined them.

---

### Post by jocko on 2007-12-17
> **toofast said:**
> dale@dale-desktop:~$ sudo dpkg --configure -a
dale@dale-desktop:~$ sudo dpkg --configure -a
dale@dale-desktop:~$ sudo dpkg --configure -a466466
dpkg: unknown option -4 ...

From what I can see the command worked the first time, there's no use to repeat it, and certainly no use in inventing new commands. The error you get is because you used the unknown option "-a666466" instead of the proper "-a".

Do you still get errors after this?
What happens if you run this in a terminal?
```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by toofast on 2007-12-17
Ok I ran what you said to run and this is what came up at the bottom it says do you want to continue do I say yes or no.


dale@dale-desktop:~$ sudo aptitude update && sudo aptitude clean && sudo aptitude dist-upgrade
Password:
Get:1 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]         
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_US       
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US       
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US              
Get:4 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release [5999B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/multiverse Sources
Fetched 6193B in 2s (2746B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  linux-headers-2.6.20-16 linux-headers-2.6.20-16-generic 
  linux-image-2.6.20-16-generic linux-restricted-modules-2.6.20-16-generic 
The following NEW packages will be installed:
  linux-headers-2.6.20-16 linux-headers-2.6.20-16-generic 
  linux-image-2.6.20-16-generic linux-restricted-modules-2.6.20-16-generic 
The following packages will be upgraded:
  app-install-data app-install-data-commercial bind9-host bsdutils cdrecord 
  cupsys cupsys-bsd cupsys-client cupsys-common dbus dbus-1-utils dnsutils 
  e2fslibs e2fsprogs evolution-data-server evolution-data-server-common 
  file firefox firefox-gnome-support foo2zjs genisoimage gimp gimp-data 
  gimp-python gnome-app-install gnome-media gnome-media-common 
  gnome-system-tools hpijs hplip hplip-data inkscape iptables kdebase-bin 
  kdebase-kio-plugins kdelibs-data kdelibs4c2a kdesktop language-pack-en 
  language-pack-gnome-en libbind9-0 libblkid1 libcairo2 libcamel1.2-10 
  libcomerr2 libcupsimage2 libcupsys2 libcurl3 libcurl3-gnutls libdbus-1-3 
  libdns22 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 
  libedataserver1.2-9 libedataserverui1.2-8 libegroupwise1.2-13 
  libexchange-storage1.2-3 libexif12 libflac7 libfreetype6 libgimp2.0 
  libgl1-mesa-dri libgl1-mesa-glx libglu1-mesa libgnome-media0 libisc11 
  libisccc0 libisccfg1 libjasper-1.701-1 libkonq4 libkpathsea4 libkrb53 
  liblwres9 libmagic1 libmagick9 libmono-cairo1.0-cil libmono-corlib1.0-cil 
  libmono-corlib2.0-cil libmono-data-tds1.0-cil libmono-data-tds2.0-cil 
  libmono-security1.0-cil libmono-security2.0-cil libmono-sharpzip0.84-cil 
  libmono-sharpzip2.84-cil libmono-sqlite1.0-cil libmono-sqlite2.0-cil 
  libmono-system-data1.0-cil libmono-system-data2.0-cil 
  libmono-system-web1.0-cil libmono-system-web2.0-cil libmono-system1.0-cil 
  libmono-system2.0-cil libmono0 libmono1.0-cil libmono2.0-cil libnspr4 
  libnss3 liboggflac3 libpcre3 libperl5.8 libpng12-0 libpoppler1 
  libpoppler1-glib libqt3-mt libsmbclient libsndfile1 libss2 libssl0.9.8 
  libt1-5 libuuid1 libvorbis0a libvorbisenc2 libvorbisfile3 libwrap0 
  libxvidcore4 linux-generic linux-headers-generic linux-image-generic 
  linux-libc-dev linux-restricted-modules-common 
  linux-restricted-modules-generic mesa-utils mkisofs mono-common mono-gac 
  mono-jit mono-runtime mount mozilla-thunderbird openoffice.org 
  openoffice.org-base openoffice.org-calc openoffice.org-common 
  openoffice.org-core openoffice.org-draw openoffice.org-evolution 
  openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk 
  openoffice.org-impress openoffice.org-java-common openoffice.org-math 
  openoffice.org-style-andromeda openoffice.org-style-default 
  openoffice.org-style-human openoffice.org-style-industrial 
  openoffice.org-writer openssl perl perl-base perl-modules poppler-utils 
  python-launchpad-bugs python-uno rsync samba-common smbclient tar tcpd 
  tcpdump ttf-opensymbol tzdata update-manager update-manager-core 
  util-linux util-linux-locales vim-common vim-tiny wodim xscreensaver-data 
  xscreensaver-gl 
173 packages upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 189MB will be used.

---

### Post by jocko on 2007-12-17
Say yes.

---

### Post by toofast on 2007-12-17
It now says this.

Writing extended state information... Error!
E: I wasn't able to locate a file for the virtualbox package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?


What should I now put in.

---

### Post by toofast on 2007-12-17
I do not know what to put for the question of am I root?:confused:

---

### Post by jocko on 2007-12-17
> **toofast said:**
> It now says this.

Writing extended state information... Error!
E: I wasn't able to locate a file for the virtualbox package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?


What should I now put in.

Do you still happen to have the virtualbox .deb file?
I guess you downloaded it from the web?
You'll probably need to complete the installation of virtualbox.

If the file is on your desktop (otherwise, move it there or download it again), what happens if you run this in a terminal:
```
cd ~/Desktop
sudo dpkg -i virtualbox*.deb
```

---

### Post by toofast on 2007-12-17
This is what pops up.

dale@dale-desktop:~$ sudo dpkg -i virtualbox*.deb
Password:
dpkg: error processing virtualbox*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 virtualbox*.deb
dale@dale-desktop:~$ 

  How do I find the virtual box program on the computer?

---

### Post by jocko on 2007-12-17
> **toofast said:**
> This is what pops up.

dale@dale-desktop:~$ sudo dpkg -i virtualbox*.deb
Password:
dpkg: error processing virtualbox*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 virtualbox*.deb
dale@dale-desktop:~$ 

  How do I find the virtual box program on the computer?

If you don't know where it is, just download it again. Place it on your desktop and run the commands from my last post again.
(I just corrected a spelling error in the first command, so if you already have the file there, try my commands again)
I won't have time to help more right now, but hopefully someone else will. I'll check later and see if you've solved it.

---

### Post by toofast on 2007-12-17
this is what I keep getting.

dpkg: error processing virtualbox*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 virtualbox*.deb


If it is saying no such file in the directory then where is it at?
I cant download anything because the dpkg error wont let me do anything I haven't been able to update my computer for months because of this problem.:confused:

I just really need to know how to get rid of this problem. I am very new to all this ubuntu stuff. I am not even the person who installed the program it was a buddy of mine who is now in a different country so he is out of the question.

I am in need of a walk through because it ios hard for me to understand stuff I have never heard of. I thank you very much for you patience with me I am sure it is hard.

---

### Post by jocko on 2007-12-17
> **toofast said:**
> this is what I keep getting.

dpkg: error processing virtualbox*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 virtualbox*.deb


If it is saying no such file in the directory then where is it at?
I cant download anything because the dpkg error wont let me do anything I haven't been able to update my computer for months because of this problem.:confused:

I just really need to know how to get rid of this problem. I am very new to all this ubuntu stuff. I am not even the person who installed the program it was a buddy of mine who is now in a different country so he is out of the question.

I am in need of a walk through because it ios hard for me to understand stuff I have never heard of. I thank you very much for you patience with me I am sure it is hard.
[URL="http://www.virtualbox.org/download/1.5.2/virtualbox_1.5.2-25433_Ubuntu_feisty_i386.deb"]
Get it from here[/URL]. (assuming you run 32 bit feisty?) Now I really don't have more time...

---

### Post by forestpixie on 2007-12-17
the only way I got that sorted when I got this

> 'E:The package virtualbox needs to be reinstalled, but I can't find an archive for it.'

was with this
```
sudo dpkg --remove --force-remove-reinstreq virtualbox
```

---

### Post by toofast on 2007-12-17
it says

Could not open.
'virtualbox_1.5.2-25433_ubuntu_feisty_i386.deb

The package might be corrupted or you are not allowed to open the file. check the permissions of the file.

Any other suggestions?

---

### Post by toofast on 2007-12-17
> **forestpixie said:**
> the only way I got that sorted when I got this



was with this
```
sudo dpkg --remove --force-remove-reinstreq virtualbox
```

after doing that it now says this.

dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 
dpkg: serious warning: files list file for package `virtualbox' missing, assuming package has no files currently installed.
111775 files and directories currently installed.)
Removing virtualbox ...

then it went back to...dale@dale-desktop:~/Desktop$  so did it do what it was supposed to do should I restart and see if it all works properly now.

---

### Post by toofast on 2007-12-17
Isn't there a way to reset it all to default? I would rather do that. the exact way it was before all this happened. Does unbuntu have a default?

---

### Post by forestpixie on 2007-12-17
it should be fine now, try 

```
sudo apt-get update
```

download the deb again and start again

---

### Post by AndyCooll on 2007-12-17
Another point to mention...follow the instructions given by joko and forestpixie to correct the error. 

However once you've finished with all that if you've managed to install VirtualBox all well and good. However as I mentioned in one of my earlier posts you **don't** need to download and install a deb, there is already a package for this in the repositories. Just open up Synaptic (System > Administration > Synaptic Package Manager) and do a search for "Virtualbox OSE". That will do install everything for you and help you avoid the type of problems you seem to have had here.

:cool:

---

