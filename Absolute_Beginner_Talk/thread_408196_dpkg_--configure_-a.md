---
title: "dpkg --configure -a"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by Nepenthesrajah on 2007-04-13
Hello,

I'm new to ubuntu, I just installed in today,  After I instilled it I clicked on the update window, it had 250 or so updates.  I was not watching but it restarted when when it rebooted it said I still had about 80 updates to install so I went to the "Software Updates window and clicked "Install Updates".  But a window popped up and said 

"An error occured

The following details are provided:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. " 

So my question is how do I run 'dpkg --configure -a'  as simple as possible since I'm such a beginner.

Thanks for your help,
-Jeremiah-

---

### Post by darkrose on 2007-04-13
open a terminal:
Applications -> Accessories -> Terminal
and type in:
sudo dpkg ---configure -a
hit enter give it your password and it should sort itself out.

---

### Post by Nepenthesrajah on 2007-04-13
Thanks for your help,

Here is what I did

"jeremiah@Ubuntu-desktop:~$ sudo dpkg ---configure -a
Password:
dpkg: unknown option ---configure

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
jeremiah@Ubuntu-desktop:~$ dpkg --help for help about installing and deinstalling packages [*]
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
jeremiah@Ubuntu-desktop:~$"

What should I do now?

thanks again,
-Jeremiah-

---

### Post by josephus on 2007-04-13
you made a typo.  there should only be two dashes

---

### Post by Nepenthesrajah on 2007-04-13
Ok thanks for catching that.  So I ran "sudo dpkg ---configure -a" and it seemed like everything was working but now when it reboots it before Ubunta is able to startup it says...

"Starting Up...
[17179571.228000] Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(0,0)
[17179571.228000]"

And it will stay a that screen forever every time I reboot.

Thanks again,
-Jeremiah-

---

### Post by jmendez2 on 2007-04-25
I am trying to do the same but the terminal will not recognize my password.  I get an authentication error.

---

