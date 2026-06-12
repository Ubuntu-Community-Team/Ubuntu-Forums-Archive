---
title: "Please help"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by Anoobiz on 2006-12-02
Does anybody have any idea on the comands for dpkg my man seems 2 be missing please guys i need sum sort of explanation for them

---

### Post by adwait on 2006-12-02
```
Reformatting dpkg(1), please wait...
DPKG(1)                           dpkg suite                           DPKG(1)



NAME
       dpkg - package manager for Debian


SYNOPSIS
       dpkg [options] action


WARNING
       This  manual is intended for users wishing to understand dpkg&#8217;s command
       line options and package states in more detail than  that  provided  by
       dpkg --help.

       It  should not be used by package maintainers wishing to understand how
       dpkg will install their packages.  The descriptions of what  dpkg  does
       when installing and removing packages are particularly inadequate.


DESCRIPTION
       dpkg  is  a  tool to install, build, remove and manage Debian packages.
       The primary and more user-friendly front-end for  dpkg  is  dselect(8).
       dpkg  itself  is controlled entirely via command line parameters, which
       consist of exactly one action and zero or  more  options.  The  action-
       parameter tells dpkg what to do and options control the behavior of the
       action in some way.

       dpkg can be also be used as a front-end to dpkg-deb.  The following are
       dpkg-deb  actions, and if they are encountered, dpkg just runs dpkg-deb
       with the parameters given to it:
           -b, --build,
           -c, --contents,
           -I, --info,
           -f, --field,
           -e, --control,
           -x, --extract,
           -X, --vextract, and
           --fsys-tarfile.
       Please refer to dpkg-deb(1) for information about these actions.


INFORMATION ABOUT PACKAGES
       dpkg maintains some usable information about  available  packages.  The
       information  is  divided in three classes: states, selection states and
       flags.  These values are intended to be changed mainly with dselect.

   PACKAGE STATES
       installed
              The package is unpacked and configured OK.

       half-installed
              The installation of the package has been started, but  not  com&#8208;
              pleted for some reason.

       not-installed
              The package is not installed on your system.

       unpacked
              The package is unpacked, but not configured.

       half-configured
              The  package is unpacked and configuration has been started, but
              not yet completed for some reason.

       config-files
              Only the configuration files of the package exist on the system.

   PACKAGE SELECTION STATES
       install
              The package is selected for installation.

       deinstall
              The  package  is  selected  for  deinstallation (i.e. we want to
              remove all files, except configuration files).

       purge  The package is selected to be purged (i.e.  we  want  to  remove
              everything, even configuration files).

   PACKAGE FLAGS
       hold   A  package  marked  to be on hold is not handled by dpkg, unless
              forced to do that with option --force-hold.

       reinst-required
              A package marked reinst-required is broken  and  requires  rein&#8208;
              stallation. These packages cannot be removed, unless forced with
              option --force-remove-reinstreq.


ACTIONS
       dpkg -i | --install package_file...
              Install the package. If --recursive or -R option  is  specified,
              package_file must refer to a directory instead.

              Installation consists of the following steps:

              1. Extract the control files of the new package.

              2.  If  another version of the same package was installed before
              the new installation, execute prerm script of the old package.

              3. Run preinst script, if provided by the package.

              4. Unpack the new files, and at the same time back  up  the  old
              files, so that if something goes wrong, they can be restored.

              5.  If  another version of the same package was installed before
              the new installation, execute the postrm script of the old pack&#8208;
              age.  Note that this script is executed after the preinst script
              of the new package, because new files are written  at  the  same
              time old files are removed.

              6.  Configure the package. See --configure for detailed informa&#8208;
              tion about how this is done.

       dpkg --unpack package_file ...
              Unpack the package, but don&#8217;t configure it. If --recursive or -R
              option  is  specified,  package_file  must  refer to a directory
              instead.

       dpkg --configure package ... | -a | --pending
              Reconfigure an unpacked package.  If -a or  --pending  is  given
              instead  of  package, all unpacked but unconfigured packages are
              configured.

              Configuring consists of the following steps:

              1. Unpack the configuration files, and at the same time back  up
              the  old  configuration  files,  so that they can be restored if
              something goes wrong.

              2. Run postinst script, if provided by the package.

       dpkg -r | --remove | -P | --purge package ... | -a | --pending
              Remove an installed package.  -r or --remove  remove  everything
              except  configuration files.  This may avoid having to reconfig&#8208;
              ure the package if  it  is  reinstalled  later.   (Configuration
              files  are  the  files  listed  in  the debian/conffiles control
              file).  -P or --purge removes everything,  including  configura&#8208;
              tion  files.   If  -a or --pending is given instead of a package
              name, then all packages unpacked, but marked to  be  removed  or
              purged  in  file  /var/lib/dpkg/status,  are  removed or purged,
              respectively.

              Removing of a package consists of the following steps:

              1. Run prerm script

              2. Remove the installed files

              3. Run postrm script

       dpkg --update-avail | --merge-avail Packages-file
              Update dpkg&#8217;s and dselect&#8217;s idea of which  packages  are  avail&#8208;
              able.   With  action  --merge-avail, old information is combined
              with    information    from    Packages-file.     With    action
              --update-avail, old information is replaced with the information
              in the Packages-file.  The Packages-file distributed with Debian
              is  simply  named  Packages.  dpkg keeps its record of available
              packages in /var/lib/dpkg/available.

              A simpler one-shot command to retrieve and update the  available
              file is dselect update.

       dpkg -A | --record-avail package_file ...
              Update  dpkg  and dselect&#8217;s idea of which packages are available
              with information from the package package_file.  If  --recursive
              or  -R  option is specified, package_file must refer to a direc&#8208;
              tory instead.

       dpkg --forget-old-unavail
              Forget about uninstalled unavailable packages.

       dpkg --clear-avail
              Erase the existing information about what  packages  are  avail&#8208;
              able.

       dpkg -C | --audit
              Searches for packages that have been installed only partially on
              your system.  dpkg will suggest what to do with them to get them
              working.

       dpkg --get-selections [package-name-pattern...]
              Get list of package selections, and write it to stdout.

       dpkg --set-selections
              Set  package  selections  using file read from stdin.  This file
              should be in the format &#8217;<package> <state>&#8217;, where state is  one
              of  install,  hold, deinstall or purge.  Blank lines and comment
              lines beginning with &#8217;#&#8217; are also permitted.

       dpkg --yet-to-unpack
              Searches for packages selected for installation, but  which  for
              some reason still haven&#8217;t been installed.


       dpkg --print-architecture
              Print   architecture   of  packages  dpkg  installs  (for
              example, "i386").

       dpkg --compare-versions ver1 op ver2
              Compare version numbers, where op is a  binary  operator.
              dpkg  returns success (zero result) if the specified con&#8208;
              dition is satisfied, and failure (nonzero result)  other&#8208;
              wise.  There are two groups of operators, which differ in
              how they treat an empty ver1 or  ver2.   These  treat  an
              empty version as earlier than any version: lt le eq ne ge
              gt.  These treat an empty version as later than any  ver&#8208;
              sion:  lt-nl  le-nl ge-nl gt-nl.  These are provided only
              for compatibility with control file syntax: < << <= =  >=
              >> >.

       dpkg --command-fd <n>
              Accept a series of commands on input file descriptor <n>.
              Note: additional options set on  the  command  line,  and
              thru  this  file descriptor, are not reset for subsequent
              commands executed during the same run.

       dpkg --help
              Display a brief help message.

       dpkg --force-help
              Give help about the --force-thing options.

       dpkg -Dh | --debug=help
              Give help about debugging options.

       dpkg --licence | dpkg --license
              Display dpkg licence.

       dpkg --version
              Display dpkg version information.

       dpkg-deb-actions
              See dpkg-deb(1) for more information about the  following
              actions.

              dpkg -b | --build directory [filename]
                  Build a deb package.
              dpkg -c | --contents filename
                  List contents of a deb package.
              dpkg -e | --control filename [directory]
                  Extract control-information from a package.
              dpkg -x | --extract filename directory
                  Extract the files contained by package.
              dpkg -f | --field  filename [control-field] ...
                  Display control field(s) of a package.
              dpkg --fsys-tarfile filename
                  Display the filesystem tar-file contained by a
                  Debian package.
              dpkg -I | --info filename [control-file]
                  Show information about a package.
              dpkg -X | --vextract filename directory
                  Extract and display the filenames contained by a
                  package.


       dpkg-query-actions
              See  dpkg-query(1) for more information about the follow&#8208;
              ing actions.


              dpkg -l | --list package-name-pattern ...
                  List packages matching given pattern.
              dpkg -s | --status package-name ...
                  Report status of specified package.
              dpkg -L | --listfiles package ...
                  List files installed to your system from package.
              dpkg -S | --search filename-search-pattern ...
                  Search for a filename from installed packages.
              dpkg -p | --print-avail package
                  Display details about package, as found in /var/lib/dpkg/available.




OPTIONS
       All options can be specified both on the commandline and in  the
       dpkg  configuration  file  /etc/dpkg/dpkg.cfg.  Each line in the
       configuration file is either an option (exactly the same as  the
       commandline  option but without leading dashes) or a comment (if
       it starts with a #).

       --abort-after=number
              Change after how many errors dpkg will abort. The default
              is 50.

       -B|--auto-deconfigure
              When  a  package  is removed, there is a possibility that
              another installed package depended on the  removed  pack&#8208;
              age.  Specifying  this option will cause automatic decon&#8208;
              figuration of the package which depended on  the  removed
              package.

       -Doctal | --debug=octal
              Set  debugging  on.   octal  is  formed by bitwise-orring
              desired values together from the list  below  (note  that
              these  values  may  change  in  future releases).  -Dh or
              --debug=help display these debugging values.

               number  description
                  1   Generally helpful progress information
                  2   Invocation and status of maintainer scripts
                 10   Output for each file processed
                100   Lots of output for each file processed
                 20   Output for each configuration file
                200   Lots of output for each configuration file
                 40   Dependencies and conflicts
                400   Lots of dependencies/conflicts output
               1000   Lots of drivel about e.g. the dpkg/info dir
               2000   Insane amounts of drivel

       --force-things | --no-force-things | --refuse-things

              Force or refuse (no-force and refuse mean the same thing)
              to  do  some things.  things is a comma separated list of
              things specified below.  --force-help displays a  message
              describing  them.   Things  marked with (*) are forced by
              default.

              Warning: These options are mostly intended to be used  by
              experts  only.  Using  them  without  fully understanding
              their effects may break your whole system.

              all: Turns on(or off) all force options.

              auto-select(*): Select packages to install them, and des&#8208;
              elect packages to remove them.

              downgrade(*): Install a package, even if newer version of
              it is already installed.

              Warning: At present  dpkg  does  not  do  any  dependency
              checking on downgrades and therefore will not warn you if
              the downgrade breaks the dependency of some  other  pack&#8208;
              age.   This  can  have  serious side effects, downgrading
              essential system components can even make your whole sys&#8208;
              tem unusable.  Use with care.

              configure-any:  Configure also any unpacked but unconfig&#8208;
              ured packages on which the current package depends.

              hold: Process packages even when marked "hold".

              remove-reinstreq: Remove a package, even if  it&#8217;s  broken
              and  marked  to  require  reinstallation.   This may, for
              example, cause parts of the package to remain on the sys&#8208;
              tem, which will then be forgotten by dpkg.

              remove-essential:  Remove, even if the package is consid&#8208;
              ered essential. Essential packages  contain  mostly  very
              basic  Unix commands. Removing them might cause the whole
              system to stop working, so use with caution.

              depends: Turn all dependency problems into warnings.

              depends-version: Don&#8217;t care about versions when  checking
              dependencies.

              conflicts:  Install,  even  if  it conflicts with another
              package. This is dangerous, for  it  will  usually  cause
              overwriting of some files.

              confmiss:  Always  install  a missing configuration file.
              This is dangerous, since it means not preserving a change
              (removing) made to the file.

              confnew:  If  a conffile has been modified always install
              the   new   version   without   prompting,   unless   the
              --force-confdef  is  also  specified,  in  which case the
              default action is preferred.

              confold: If a conffile has been modified always keep  the
              old version without prompting, unless the --force-confdef
              is also specified, in which case the  default  action  is
              preferred.

              confdef:  If  a  conffile has been modified always choose
              the default action. If there is no default action it will
              stop   to   ask   the   user  unless  --force-confnew  or
              --force-confold is also been given, in which case it will
              use that to decide the final action.

              overwrite:  Overwrite  one  package&#8217;s file with another&#8217;s
              file.

              overwrite-dir  Overwrite  one  package&#8217;s  directory  with
              another&#8217;s file.

              overwrite-diverted:  Overwrite  a  diverted  file with an
              undiverted version.

              architecture: Process even packages with the wrong archi&#8208;
              tecture.

              bad-path: PATH is missing important programs, so problems
              are likely.

              not-root: Try to (de)install things even when not root.

              bad-verify: Install a package even if it fails authentic&#8208;
              ity check.


       --ignore-depends=package,...
              Ignore  dependency-checking for specified packages (actu&#8208;
              ally, checking is performed, but only warnings about con&#8208;
              flicts are given, nothing else).

       --new | --old
              Select  new  or  old  binary  package  format.  This is a
              dpkg-deb(1) option.

       --nocheck
              Don&#8217;t read or check contents of control file while build&#8208;
              ing a package.  This is a dpkg-deb(1) option.

       --no-act | --dry-run | --simulate
              Do  everything  which  is  supposed to be done, but don&#8217;t
              write any changes. This is used to see what would  happen
              with  the  specified  action,  without actually modifying
              anything.

              Be sure to give --no-act before the action-parameter,  or
              you  might  end up with undesirable results.  (e.g.  dpkg
              --purge foo --no-act will first  purge  package  foo  and
              then try to purge package --no-act, even though you prob&#8208;
              ably expected it to actually do nothing)

       -R | --recursive
              Recursively handle all  regular  files  matching  pattern
              *.deb  found at specified directories and all of its sub&#8208;
              directories. This can be used  with  -i,  -A,  --install,
              --unpack and --avail actions.

       -G     Don&#8217;t  install  a  package if a newer version of the same
              package  is  already  installed.  This  is  an  alias  of
              --refuse-downgrade.

       --root=dir | --admindir=dir | --instdir=dir
              Change   default   directories.    admindir  defaults  to
              /var/lib/dpkg and contains many files that give  informa&#8208;
              tion  about  status of installed or uninstalled packages,
              etc.  instdir defaults to / and refers to  the  directory
              where  packages are to be installed.  instdir is also the
              directory passed to chroot(2)  before  running  package&#8217;s
              installation  scripts,  which  means that the scripts see
              instdir as a root directory.  Changing root changes inst&#65533;
              dir to dir and admindir to dir/var/lib/dpkg.

       -O | --selected-only
              Only process the packages that are selected for installa&#8208;
              tion. The actual marking is done with dselect or by dpkg,
              when it handles packages.  For example, when a package is
              removed, it will be marked selected for deinstallation.

       -E | --skip-same-version
              Don&#8217;t install the package if  the  same  version  of  the
              package is already installed.

       --status-fd <n>
              Send  package  status  info to file descriptor <n>.  This
              can be given multiple times.  Status updates are  of  the
              form  &#8216;status: <pkg>: <pkg qstate>&#8217;.  Errors are reported
              as &#8216;status: <pkg>: error: extend-error-message&#8217;.  Config&#8208;
              uration file conflicts are reported as &#8216;status: conffile-
              prompt:  conffile  :  &#8217;current-conffile&#8217;   &#8217;new-conffile&#8217;
              useredited distedited&#8217;

       --log=filename
              Log  status change updates and actions to filename.  This
              can be given multiple times.  Log  messages  are  of  the
              form    &#8216;YYYY-MM-DD   HH:MM:SS   status   <state>   <pkg>
              <installed-version>&#8217; for status change updates; &#8216;YYYY-MM-
              DD  HH:MM:SS  <action>  <pkg> <installed-version> <avail&#8208;
              able-version>&#8217; for  actions  where  <action>  is  one  of
              install, upgrade, remove, purge; and &#8216;YYYY-MM-DD HH:MM:SS
              conffile  <filename>  <decision>&#8217;  for  conffile  changes
              where <decision is either install or keep.

FILES
       /etc/dpkg/dpkg.cfg
              Configuration file with default options.

       The  other  files listed below are in their default directories,
       see option --admindir to see how to change  locations  of  these
       files.

       /var/lib/dpkg/available
              List of available packages.

       /var/lib/dpkg/status
              Statuses of available packages. This file contains infor&#8208;
              mation about whether a package is marked for removing  or
              not,  whether  it  is  installed or not, etc. See section
              INFORMATION ABOUT PACKAGES for more info.

       The following files are components of  a  binary  package.   See
       deb(5) for more information about them:

       control

       conffiles

       preinst

       postinst

       prerm

       postrm

ENVIRONMENT VARIABLES
       DPKG_NO_TSTP
              Define  this  to  something if you prefer dpkg starting a
              new shell rather than suspending itself,  while  doing  a
              shell escape.

       SHELL  The program dpkg will execute while starting a new shell.

       COLUMNS
              Sets the number of columns dpkg should use when  display&#8208;
              ing formatted text.  Currently only used by -l.

       DPKG_OLD_CONFFILE
              Set by dpkg to the filename of the old configuration file
              when you start a shell to examine  a  changed  configura&#8208;
              tion.  file.

       DPKG_NEW_CONFFILE
              Set  by  dpkg to the filename of the newversion of a con&#8208;
              figuration file when you  start  a  shell  to  examine  a
              changed configuration.  file.


EXAMPLES
       To list packages related to the editor vi:
            dpkg -l &#65533;*vi*&#65533;

       To see the entries in /var/lib/dpkg/available on two packages:
            dpkg --print-avail elvis vim | less

       To search the listing of packages yourself:
            less /var/lib/dpkg/available

       To remove an installed elvis package:
            dpkg -r elvis

       To install a package, you first need to find it in an archive or
       CDROM.  The "available" file shows that the vim  package  is  in
       section "editors":
            cd /cdrom/hamm/hamm/binary/editors
            dpkg -i vim_4.5-3.deb

       To make a local copy of the package selection states:
            dpkg --get-selections >myselections

       You might transfer this file to another computer, and install it
       there with:
            dpkg --set-selections <myselections
       Note that this will not actually install or remove anything, but
       just  set  the  selection  state on the requested packages.  You
       will need  some  other  application  to  actually  download  and
       install  the  requested  packages.  For example, run dselect and
       choose "Install".

       Ordinarily, you will find that dselect(8) provides a more conve&#8208;
       nient way to modify the package selection states.

ADDITIONAL FUNCTIONALITY
       Additional  functionality can be gained by installing any of the
       following packages: apt, aptitude and debsums.


SEE ALSO
       dselect(8), dpkg-deb(1), deb(5), deb-control(5), and dpkg-recon&#65533;
       figure(8)


BUGS
       --no-act usually gives less information than might be helpful.


AUTHORS
       See /usr/share/doc/dpkg/THANKS.gz for the list of people who have
       contributed to dpkg .



Debian Project                  April 12, 1998                         DPKG(1)
```

There you go, my man entry for dpkg

---

