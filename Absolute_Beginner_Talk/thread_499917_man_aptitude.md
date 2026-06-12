---
title: "man aptitude"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by hannulan on 2007-07-13
I have no acces to a computer with Ubuntu installed for the moment, but I would like to read the man pages for aptitude. Can't find them (or at least any recent version of them) on the internet. Can someone help me with it? I guess it's simple just that I'm blind for the moment.

---

### Post by smoker on 2007-07-13
is this what you're looking for?
[http://nixdoc.net/man-pages/Linux/man1/aptitude.1.html](http://nixdoc.net/man-pages/Linux/man1/aptitude.1.html)

---

### Post by hannulan on 2007-07-13
Yes, but this one is from 2000. Is it still correct? I guess not when I found it.  The question I try to answer is what apt-get autoremove do. Yes I know aptitude and apt-get is not the same thing, I wrote wrong before. But I have the same problem finding a new man page for apt-get as for aptitude.

---

### Post by overdrank on 2007-07-13
> **hannulan said:**
> Yes, but this one is from 2000. Is it still correct? I guess not when I found it.  The question I try to answer is what apt-get autoremove do. Yes I know aptitude and apt-get is not the same thing, I wrote wrong before. But I have the same problem finding a new man page for apt-get as for aptitude.
HI how about this page
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)
:popcorn:

---

### Post by smoker on 2007-07-13
hi, sorry if that link was out of date (i really need to update my bookmark!),

this is a download of man pages, though i don't know how updated it is, i have never used it, so trial and error i think, but hopefully some use to you:
[http://tldp.org/manpages/man.php](http://tldp.org/manpages/man.php)

---

### Post by davidjmayo on 2007-07-13
delete

---

### Post by KIAaze on 2007-07-13
I extracted it from the latest .deb package from packages.ubuntu.com/ **(aptitude_0.4.4-1ubuntu3_i386.deb)** and printed it out on the terminal using:
```
man -M <path to extracted deb>/usr/share/man aptitude
```

There you go:
> APTITUDE(8 )                 Command-Line Reference                 APTITUDE(8 )



NAME
       aptitude - high-level interface to the package manager

SYNOPSIS
       aptitude [<options>...] {autoclean | clean | forget-new | keep-all |
                update | upgrade}

       aptitude [<options>...] {changelog | dist-upgrade | download |
                forbid-version | hold | install | keep-all | markauto | purge
                | reinstall | remove | show | unhold | unmarkauto}
                <packages>...

       aptitude [<options>...] search <patterns>...

       aptitude [-S <fname>] [-u | -i]

       aptitude help

DESCRIPTION
       aptitude is a text-based interface to the Debian GNU/Linux package
       system.

       It allows the user to view the list of packages and to perform package
       management tasks such as installing, upgrading, and removing packages.
       Actions may be performed from a visual interface or from the
       command-line.

COMMAND-LINE ACTIONS
       The first argument which does not begin with a hyphen ("-") is
       considered to be an action that the program should perform. If an
       action is not specified on the command-line, aptitude will start up in
       visual mode.

       The following actions are available:

       install
          Install one or more packages. The packages should be listed after
          the "install" command; if a package name contains a tilde character
          ("~"), it will be treated as a search pattern and every package
          matching the pattern will be installed (see the section "Search
          Patterns" in the aptitude reference manual).

          To select a particular version of the package, append "=<version>"
          to the package name: for instance, "aptitude install apt=0.3.1".
          Similarly, to select a package from a particular archive, append
          "/<archive>" to the package name: for instance, "aptitude install
          apt/experimental".

          Not every package listed on the command line has to be installed;
          you can tell aptitude to do something different with a package by
          appending an "override specifier" to the name of the package. For
          example, aptitude remove wesnoth+ will install wesnoth, not remove
          it. The following override specifiers are available:

             <package>+
                Install <package>.

             <package>+M
                Install <package> and immediately mark it as automatically
                installed (note that if nothing depends on <package>, this
                will cause it to be immediately removed).

             <package>-
                Remove <package>.

             <package>_
                Purge <package>: remove it and all its associated
                configuration and data files.

             <package>=
                Place <package> on hold: cancel any active installation,
                upgrade, or removal, and prevent this package from being
                automatically upgraded in the future.

             <package>:
                Keep <package> at its current version: cancel any
                installation, removal, or upgrade. Unlike "hold" (above) this
                does not prevent automatic upgrades in the future.

             <package>&M
                Mark <package> as having been automatically installed.

             <package>&m
                Mark <package> as having been manually installed.

             As a special case, "install" with no arguments will act on any
             stored/pending actions.

             Note
             Once you enter Y at the final confirmation prompt, the "install"
             command will modify aptitude's stored information about what
             actions to perform. Therefore, if you issue (e.g.) the command
             "aptitude install foo bar" and then abort the installation once
             aptitude has started downloading and installing packages, you
             will need to run "aptitude remove foo bar" to cancel that order.

       remove, purge, hold, unhold, keep, reinstall
          These commands are the same as "install", but apply the named action
          to all packages given on the command line for which it is not
          overridden. The difference between hold and keep is that hold will
          cause a package to be ignored by future upgrade commands, while keep
          merely cancels any scheduled actions on the package.  unhold will
          cause a package to be upgraded by future upgrade commands, without
          otherwise altering its state.

          For instance, "aptitude remove '~ndeity'" will remove all packages
          whose name contains "deity".

       markauto, unmarkauto
          Mark packages as automatically installed or manually installed,
          respectively. Packages are specified in exactly the same way as for
          the "install" command. For instance, "aptitude markauto '~slibs'"
          will mark all packages in the "libs" section as having been
          automatically installed.

          For more information on automatically installed packages, see the
          section "Managing Automatically Installed Packages" in the aptitude
          reference manual.

       forbid-version
          Forbid a package from being upgraded to a particular version. This
          will prevent aptitude from automatically upgrading to this version,
          but will allow automatic upgrades to future versions. By default,
          aptitude will select the version to which the package would normally
          be upgraded; you may override this selection by appending
          "=<version>" to the package name: for instance, "aptitude
          forbid-version vim=1.2.3.broken-4".

          This command is useful for avoiding broken versions of packages
          without having to set and clear manual holds. If you decide you
          really want the forbidden version after all, the "install" command
          will remove the ban.

       update
          Updates the list of available packages from the apt sources (this is
          equivalent to "apt-get update")

       upgrade
          Upgrades installed packages to their most recent version. Installed
          packages will not be removed unless they are unused (see the section
          "Managing Automatically Installed Packages" in the aptitude
          reference manual); packages which are not currently installed will
          not be installed.

          If a package cannot be upgraded without violating these constraints,
          it will be kept at its current version. Use the dist-upgrade command
          to upgrade these packages as well.

       dist-upgrade
          Upgrades installed packages to their most recent version, removing
          or installing packages as necessary. This command is less
          conservative than upgrade and thus more likely to perform unwanted
          actions. Users are advised to either use upgrade instead or to
          carefully inspect the list of packages to be installed and removed.

       keep-all
          Cancels all scheduled actions on all packages; any packages whose
          sticky state indicates an installation, removal, or upgrade will
          have this sticky state cleared.

       forget-new
          Forgets all internal information about what packages are "new"
          (equivalent to pressing "f" when in visual mode).

       search
          Searches for packages matching one of the patterns supplied on the
          command line. All packages which match any of the given patterns
          will be displayed; for instance, "aptitude search '~N'" will list
          all "new" packages. For more information on search patterns, see the
          section "Search Patterns" in the aptitude reference manual.

          Unless you pass the -F option, the output of aptitude search will
          look something like this:

             i   apt                             - Advanced front-end for dpkg
             pi  apt-build                       - frontend to apt to build, optimize and in
             cp  apt-file                        - APT package searching utility -- command-
             ihA raptor-utils                    - Raptor RDF Parser utilities
          Each search result is listed on a separate line. The first character
          of each line indicates the current state of the package: the most
          common states are p, meaning that no trace of the package exists on
          the system, c, meaning that the package was deleted but its
          configuration files remain on the system, i, meaning that the
          package is installed, and v, meaning that the package is virtual.
          The second character indicates the stored action (if any; otherwise
          a blank space is displayed) to be performed on the package, with the
          most common actions being i, meaning that the package will be
          installed, d, meaning that the package will be deleted, and p,
          meaning that the package and its configuration files will be
          removed. If the third character is A, the package was automatically
          installed.

          For a complete list of the possible state and action flags, see the
          section "Accessing Package Information" in the aptitude reference
          guide.

       show
          Displays detailed information about one or more packages, listed
          following the search command. If a package name contains a tilde
          character ("~"), it will be treated as a search pattern and all
          matching packages will be displayed (see the section "Search
          Patterns" in the aptitude reference manual).

          If the verbosity level is 1 or greater (i.e., at least one -v is
          present on the command-line), information about all versions of the
          package is displayed. Otherwise, information about the "candidate
          version" (the version that "aptitude install" would download) is
          displayed.

          You can display information about a different version of the package
          by appending =<version> to the package name; you can display the
          version from a particular archive by appending /<archive> to the
          package name. If either of these is present, then only the version
          you request will be displayed, regardless of the verbosity level.

          If the verbosity level is 1 or greater, the package's architecture,
          compressed size, filename, and md5sum fields will be displayed. If
          the verbosity level is 2 or greater, the select version or versions
          will be displayed once for each archive in which they are found.

       clean
          Removes all previously downloaded .deb files from the package cache
          directory (usually /var/cache/apt/archives).

       autoclean
          Removes any cached packages which can no longer be downloaded. This
          allows you to prevent a cache from growing out of control over time
          without completely emptying it.

       changelog
          Downloads and displays the Debian changelog for each of the given
          source or binary packages.

          By default, the changelog for the version which would be installed
          with "aptitude install" is downloaded. You can select a particular
          version of a package by appending =<version> to the package name;
          you can select the version from a particular archive by appending
          /<archive> to the package name.

       download
          Downloads the .deb file for the given package to the current
          directory.

          By default, the version which would be installed with "aptitude
          install" is downloaded. You can select a particular version of a
          package by appending =<version> to the package name; you can select
          the version from a particular archive by appending /<archive> to the
          package name.

       help
          Displays a brief summary of the available commands and options.

OPTIONS
       The following options may be used to modify the behavior of the actions
       described above. Note that while all options will be accepted for all
       commands, some options don't apply to particular commands and will be
       ignored by those commands.

       -D, --show-deps
          For commands that will install or remove packages (install, upgrade,
          etc), show brief explanations of automatic installations and
          removals.

          This corresponds to the configuration option
          Aptitude::CmdLine::Show-Deps.

       -d, --download-only
          Download packages to the package cache as necessary, but do not
          install or remove anything. By default, the package cache is stored
          in /var/cache/apt/archives.

          This corresponds to the configuration option
          Aptitude::CmdLine:: Download-Only.

       -F <format>, --display-format <format>
          Specify the format which should be used to display output from the
          search command. For instance, passing "%p %V %v" for <format> will
          display a package's name, followed by its currently installed
          version and its available version (see the section "Customizing how
          packages are displayed" in the aptitude reference manual for more
          information).

          This corresponds to the configuration option
          Aptitude::CmdLine::Package-Display-Format.

       -f
          Try hard to fix the dependencies of broken packages, even if it
          means ignoring the actions requested on the command line.

          This corresponds to the configuration item
          Aptitude::CmdLine::Fix-Broken.

       -h, --help
          Display a brief help message. Identical to the help action.

       --purge-unused
          Purge packages that are no longer required by any installed package.
          This is equivalent to passing "-o Aptitude::Purge-Unused=true" as a
          command-line argument.

       -P, --prompt
          Always display a prompt, even when no actions other than those
          explicitly requested will be performed.

          This corresponds to the configuration option
          Aptitude::CmdLine::Always-Prompt.

       -R, --without-recommends
          Do not treat recommendations as dependencies when installing new
          packages (this overrides settings in /etc/apt/apt.conf and
          ~/.aptitude/config).

          This corresponds to the configuration option
          Aptitude::Recommends-Important

       -r, --with-recommends
          Treat recommendations as dependencies when installing new packages
          (this overrides settings in /etc/apt/apt.conf and
          ~/.aptitude/config).

          This corresponds to the configuration option
          Aptitude::Recommends-Important

       -s, --simulate
          In command-line mode, print the actions that would normally be
          performed, but don't actually perform them. This does not require
          root privileges. In the visual interface, always open the cache in
          read-only mode regardless of whether you are root.

          This corresponds to the configuration option Aptitude::Simulate.

       --schedule-only
          For commands that modify package states, schedule operations to be
          performed in the future, but don't perform them. You can execute
          scheduled actions by running aptitude install with no arguments.
          This is equivalent to making the corresponding selections in visual
          mode, then exiting the program normally.

          For instance, aptitude --schedule-only install evolution will
          schedule the evolution package for later installation.

       -t <release>, --target-release <release>
          Set the release from which packages should be installed. For
          instance, "aptitude -t experimental ..."  will install packages from
          the experimental distribution unless you specify otherwise. For the
          command-line actions "changelog", "download", and "show", this is
          equivalent to appending /<release> to each package named on the
          command-line; for other commands, this will affect the default
          candidate version of packages according to the rules described in
          apt_preferences(5).

          This corresponds to the configuration item APT:: Default-Release.

       -O <order>, --sort <order>
          Specify the order in which output from the search command should be
          displayed. For instance, passing "installsize" for <order> will list
          packages in order according to their size when installed (see the
          section "Customizing how packages are sorted" in the aptitude
          reference manual for more information).

       -o <key>=<value>
          Set a configuration file option directly; for instance, use -o
          Aptitude::Log=/tmp/my-log to log aptitude's actions to /tmp/my-log.
          For more information on configuration file options, see the section
          "Configuration file reference" in the aptitude reference manual.

       -q[=<n>], --quiet[=<n>]
          Suppress all incremental progress indicators, thus making the output
          loggable. This may be supplied multiple times to make the program
          quieter, but unlike apt-get, aptitude does not enable -y when -q is
          supplied more than once.

          The optional =<n> may be used to directly set the amount of
          quietness (for instance, to override a setting in
          /etc/apt/apt.conf); it causes the program to behave as if -q had
          been passed exactly <n> times.

       -V, --show-versions
          Show which versions of packages will be installed.

          This corresponds to the configuration option
          Aptitude::CmdLine::Show-Versions.

       -v, --verbose
          Causes some commands (for instance, show) to display extra
          information. This may be supplied multiple times to get more and
          more information.

          This corresponds to the configuration option
          Aptitude::CmdLine::Verbose.

       --version
          Display the version of aptitude and some information about how it
          was compiled.

       --visual-preview
          When installing or removing packages from the command line, instead
          of displaying the usual prompt, start up the visual interface and
          display its preview screen.

       -w <width>, --width <width>
          Specify the display width which should be used for output from the
          search command (by default, the terminal width is used).

          This corresponds to the configuration option
          Aptitude::CmdLine::Package-Display-Width

       -y, --assume-yes
          When a yes/no prompt would be presented, assume that the user
          entered "yes". In particular, suppresses the prompt that appears
          when installing, upgrading, or removing packages. Prompts for
          "dangerous" actions, such as removing essential packages, will still
          be displayed. This option overrides -P.

          This corresponds to the configuration option
          Aptitude::CmdLine::Assume-Yes.

       -Z
          Show how much disk space will be used or freed by the individual
          packages being installed, upgraded, or removed.

          This corresponds to the configuration option
          Aptitude::CmdLine::Show-Size-Changes.

       The following options apply to the visual mode of the program, but are
       primarily for internal use; you generally won't need to use them
       yourself.

       -S <fname>
          Loads the extended state information from <fname> instead of the
          standard state file.

       -u
          Begins updating the package lists as soon as the program starts. You
          cannot use this option and -i at the same time.

       -i
          Displays a download preview when the program starts (equivalent to
          starting the program and immediately pressing "g"). You cannot use
          this option and "-u" at the same time.

ENVIRONMENT
       HOME
          If $HOME/.aptitude exists, aptitude will store its configuration
          file in $HOME/.aptitude/config. Otherwise, it will look up the
          current user's home directory using getpwuid(2) and place its
          configuration file there.

       PAGER
          If this environment variable is set, aptitude will use it to display
          changelogs when "aptitude changelog" is invoked. If not set, it
          defaults to more.

       TMP
          If TMPDIR is unset, aptitude will store its temporary files in TMP
          if that variable is set. Otherwise, it will store them in /tmp.

       TMPDIR

          aptitude will store its temporary files in the directory indicated
          by this environment variable. If TMPDIR is not set, then TMP will be
          used; if TMP is also unset, then aptitude will use /tmp.

SEE ALSO
       apt-get(8 ), apt(8 ), /usr/share/doc/aptitude/html/<lang>/index.html from
       the package aptitude-doc-<lang>

AUTHORS
       Daniel Burrows <dburrows@debian.org>
          Author.

       Daniel Burrows <dburrows@debian.org>
          Author.

COPYRIGHT
       This manual page is free software; you can redistribute it and/or
       modify it under the terms of the GNU General Public License as
       published by the Free Software Foundation; either version 2 of the
       License, or (at your option) any later version.

       This manual page is distributed in the hope that it will be useful, but
       WITHOUT ANY WARRANTY; without even the implied warranty of
       MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
       General Public License for more details.

       You should have received a copy of the GNU General Public License along
       with this manual page; if not, write to the Free Software Foundation,
       Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA



                                  02/26/2007                       APTITUDE(8 )


---

### Post by KIAaze on 2007-07-13
From **apt_0.6.46.4ubuntu10_i386.deb** :
> APT-GET(8 )                                                          APT-GET(8 )



NAME
       apt-get - APT package handling utility -- command-line interface

SYNOPSIS
       apt-get [-hvs] [-o=config string] [-c=file] {[update] | [upgrade] |
               [dselect-upgrade] | [install pkg...] | [remove pkg...] |
               [source pkg...] | [build-dep pkg...] | [check] | [clean] |
               [autoclean] | [autoremove]}

DESCRIPTION
       apt-get is the command-line tool for handling packages, and may be
       considered the user's "back-end" to other tools using the APT library.
       Several "front-end" interfaces exist, such as dselect(8 ), aptitude,
       synaptic, gnome-apt and wajig.

       Unless the -h, or --help option is given, one of the commands below
       must be present.

       update
          update is used to resynchronize the package index files from their
          sources. The indexes of available packages are fetched from the
          location(s) specified in /etc/apt/sources.list. For example, when
          using a Debian archive, this command retrieves and scans the
          Packages.gz files, so that information about new and updated
          packages is available. An update should always be performed before
          an upgrade or dist-upgrade. Please be aware that the overall
          progress meter will be incorrect as the size of the package files
          cannot be known in advance.

       upgrade
          upgrade is used to install the newest versions of all packages
          currently installed on the system from the sources enumerated in
          /etc/apt/sources.list. Packages currently installed with new
          versions available are retrieved and upgraded; under no
          circumstances are currently installed packages removed, or packages
          not already installed retrieved and installed. New versions of
          currently installed packages that cannot be upgraded without
          changing the install status of another package will be left at their
          current version. An update must be performed first so that apt-get
          knows that new versions of packages are available.

       dselect-upgrade
          dselect-upgrade is used in conjunction with the traditional Debian
          packaging front-end, dselect(8 ).  dselect-upgrade follows the
          changes made by dselect(8 ) to the Status field of available
          packages, and performs the actions necessary to realize that state
          (for instance, the removal of old and the installation of new
          packages).

       dist-upgrade
          dist-upgrade in addition to performing the function of upgrade, also
          intelligently handles changing dependencies with new versions of
          packages; apt-get has a "smart" conflict resolution system, and it
          will attempt to upgrade the most important packages at the expense
          of less important ones if necessary. The /etc/apt/sources.list file
          contains a list of locations from which to retrieve desired package
          files. See also apt_preferences(5) for a mechanism for overriding
          the general settings for individual packages.

       install
          install is followed by one or more packages desired for
          installation. Each package is a package name, not a fully qualified
          filename (for instance, in a Debian GNU/Linux system, libc6 would be
          the argument provided, not libc6_1.9.6-2.deb) All packages required
          by the package(s) specified for installation will also be retrieved
          and installed. The /etc/apt/sources.list file is used to locate the
          desired packages. If a hyphen is appended to the package name (with
          no intervening space), the identified package will be removed if it
          is installed. Similarly a plus sign can be used to designate a
          package to install. These latter features may be used to override
          decisions made by apt-get's conflict resolution system.

          A specific version of a package can be selected for installation by
          following the package name with an equals and the version of the
          package to select. This will cause that version to be located and
          selected for install. Alternatively a specific distribution can be
          selected by following the package name with a slash and the version
          of the distribution or the Archive name (stable, testing, unstable).

          Both of the version selection mechanisms can downgrade packages and
          must be used with care.

          Finally, the apt_preferences(5) mechanism allows you to create an
          alternative installation policy for individual packages.

          If no package matches the given expression and the expression
          contains one of '.', '?' or '*' then it is assumed to be a POSIX
          regular expression, and it is applied to all package names in the
          database. Any matches are then installed (or removed). Note that
          matching is done by substring so 'lo.*' matches 'how-lo' and
          'lowest'. If this is undesired, anchor the regular expression with a
          '^' or '$' character, or create a more specific regular expression.

       remove
          remove is identical to install except that packages are removed
          instead of installed. If a plus sign is appended to the package name
          (with no intervening space), the identified package will be
          installed instead of removed.

       source
          source causes apt-get to fetch source packages. APT will examine the
          available packages to decide which source package to fetch. It will
          then find and download into the current directory the newest
          available version of that source package. Source packages are
          tracked separately from binary packages via deb-src type lines in
          the sources.list(5) file. This probably will mean that you will not
          get the same source as the package you have installed or as you
          could install. If the --compile options is specified then the
          package will be compiled to a binary .deb using dpkg-buildpackage,
          if --download-only is specified then the source package will not be
          unpacked.

          A specific source version can be retrieved by postfixing the source
          name with an equals and then the version to fetch, similar to the
          mechanism used for the package files. This enables exact matching of
          the source package name and version, implicitly enabling the
          APT::Get::Only-Source option.

          Note that source packages are not tracked like binary packages, they
          exist only in the current directory and are similar to downloading
          source tar balls.

       build-dep
          build-dep causes apt-get to install/remove packages in an attempt to
          satisfy the build dependencies for a source package.

       check
          check is a diagnostic tool; it updates the package cache and checks
          for broken dependencies.

       clean
          clean clears out the local repository of retrieved package files. It
          removes everything but the lock file from /var/cache/apt/archives/
          and /var/cache/apt/archives/partial/. When APT is used as a
          dselect(8 ) method, clean is run automatically. Those who do not use
          dselect will likely want to run apt-get clean from time to time to
          free up disk space.

       autoclean
          Like clean, autoclean clears out the local repository of retrieved
          package files. The difference is that it only removes package files
          that can no longer be downloaded, and are largely useless. This
          allows a cache to be maintained over a long period without it
          growing out of control. The configuration option
          APT::Clean-Installed will prevent installed packages from being
          erased if it is set to off.

       autoremove
          autoremove is used to remove packages that were automatically
          installed to satisfy dependencies for some package and that are no
          more needed.

OPTIONS
       All command line options may be set using the configuration file, the
       descriptions indicate the configuration option to set. For boolean
       options you can override the config file by using something like
       -f-,--no-f, -f=no or several other variations.

       -d, --download-only
          Download only; package files are only retrieved, not unpacked or
          installed. Configuration Item: APT::Get:: Download-Only.

       -f, --fix-broken
          Fix; attempt to correct a system with broken dependencies in place.
          This option, when used with install/remove, can omit any packages to
          permit APT to deduce a likely solution. Any Package that are
          specified must completely correct the problem. The option is
          sometimes necessary when running APT for the first time; APT itself
          does not allow broken package dependencies to exist on a system. It
          is possible that a system's dependency structure can be so corrupt
          as to require manual intervention (which usually means using
          dselect(8 ) or dpkg --remove to eliminate some of the offending
          packages). Use of this option together with -m may produce an error
          in some situations. Configuration Item: APT::Get::Fix-Broken.

       -m, --ignore-missing, --fix-missing
          Ignore missing packages; If packages cannot be retrieved or fail the
          integrity check after retrieval (corrupted package files), hold back
          those packages and handle the result. Use of this option together
          with -f may produce an error in some situations. If a package is
          selected for installation (particularly if it is mentioned on the
          command line) and it could not be downloaded then it will be
          silently held back. Configuration Item: APT::Get::Fix-Missing.

       --no-download
          Disables downloading of packages. This is best used with
          --ignore-missing to force APT to use only the .debs it has already
          downloaded. Configuration Item: APT::Get:: Download.

       -q, --quiet
          Quiet; produces output suitable for logging, omitting progress
          indicators. More q's will produce more quiet up to a maximum of 2.
          You can also use -q=# to set the quiet level, overriding the
          configuration file. Note that quiet level 2 implies -y, you should
          never use -qq without a no-action modifier such as -d, --print-uris
          or -s as APT may decided to do something you did not expect.
          Configuration Item: quiet.

       -s, --simulate, --just-print, --dry-run, --recon, --no-act
          No action; perform a simulation of events that would occur but do
          not actually change the system. Configuration Item:
          APT::Get::Simulate.

          Simulate prints out a series of lines each one representing a dpkg
          operation, Configure (Conf), Remove (Remv), Unpack (Inst). Square
          brackets indicate broken packages with and empty set of square
          brackets meaning breaks that are of no consequence (rare).

       -y, --yes, --assume-yes
          Automatic yes to prompts; assume "yes" as answer to all prompts and
          run non-interactively. If an undesirable situation, such as changing
          a held package, trying to install a unauthenticated package or
          removing an essential package occurs then apt-get will abort.
          Configuration Item: APT::Get::Assume-Yes.

       -u, --show-upgraded
          Show upgraded packages; Print out a list of all packages that are to
          be upgraded. Configuration Item: APT::Get::Show-Upgraded.

       -V, --verbose-versions
          Show full versions for upgraded and installed packages.
          Configuration Item: APT::Get::Show-Versions.

       -b, --compile, --build
          Compile source packages after downloading them. Configuration Item:
          APT::Get::Compile.

       --ignore-hold
          Ignore package Holds; This causes apt-get to ignore a hold placed on
          a package. This may be useful in conjunction with dist-upgrade to
          override a large number of undesired holds. Configuration Item:
          APT::Ignore-Hold.

       --no-upgrade
          Do not upgrade packages; When used in conjunction with install,
          no-upgrade will prevent packages on the command line from being
          upgraded if they are already installed. Configuration Item:
          APT::Get::Upgrade.

       --force-yes
          Force yes; This is a dangerous option that will cause apt to
          continue without prompting if it is doing something potentially
          harmful. It should not be used except in very special situations.
          Using force-yes can potentially destroy your system! Configuration
          Item: APT::Get::force-yes.

       --print-uris
          Instead of fetching the files to install their URIs are printed.
          Each URI will have the path, the destination file name, the size and
          the expected md5 hash. Note that the file name to write to will not
          always match the file name on the remote site! This also works with
          the source and update commands. When used with the update command
          the MD5 and size are not included, and it is up to the user to
          decompress any compressed files. Configuration Item:
          APT::Get::Print-URIs.

       --purge
          Use purge instead of remove for anything that would be removed. An
          asterisk ("*") will be displayed next to packages which are
          scheduled to be purged. Configuration Item: APT::Get::Purge.

       --reinstall
          Re-Install packages that are already installed and at the newest
          version. Configuration Item: APT::Get::ReInstall.

       --list-cleanup
          This option defaults to on, use --no-list-cleanup to turn it off.
          When on apt-get will automatically manage the contents of
          /var/lib/apt/lists to ensure that obsolete files are erased. The
          only reason to turn it off is if you frequently change your source
          list. Configuration Item: APT::Get::List-Cleanup.

       -t, --target-release, --default-release
          This option controls the default input to the policy engine, it
          creates a default pin at priority 990 using the specified release
          string. The preferences file may further override this setting. In
          short, this option lets you have simple control over which
          distribution packages will be retrieved from. Some common examples
          might be -t '2.1*' or -t unstable. Configuration Item:
          APT:: Default-Release; see also the apt_preferences(5) manual page.

       --trivial-only
          Only perform operations that are 'trivial'. Logically this can be
          considered related to --assume-yes, where --assume-yes will answer
          yes to any prompt, --trivial-only will answer no. Configuration
          Item: APT::Get::Trivial-Only.

       --no-remove
          If any packages are to be removed apt-get immediately aborts without
          prompting. Configuration Item: APT::Get::Remove.

       --auto-remove
          If the command is either install or remove, then this option acts
          like running autoremove command, removing the unused dependency
          packages. Configuration Item: APT::Get::AutomaticRemove.

       --only-source
          Only has meaning for the source and build-dep commands. Indicates
          that the given source names are not to be mapped through the binary
          table. This means that if this option is specified, these commands
          will only accept source package names as arguments, rather than
          accepting binary package names and looking up the corresponding
          source package. Configuration Item: APT::Get::Only-Source.

       --diff-only, --tar-only
          Download only the diff or tar file of a source archive.
          Configuration Item: APT::Get:: Diff-Only and APT::Get::Tar-Only.

       --arch-only
          Only process architecture-dependent build-dependencies.
          Configuration Item: APT::Get::Arch-Only.

       --allow-unauthenticated
          Ignore if packages can't be authenticated and don't prompt about it.
          This is usefull for tools like pbuilder. Configuration Item:
          APT::Get::AllowUnauthenticated.

       -h, --help
          Show a short usage summary.

       -v, --version
          Show the program version.

       -c, --config-file
          Configuration File; Specify a configuration file to use. The program
          will read the default configuration file and then this configuration
          file. See apt.conf(5) for syntax information.

       -o, --option
          Set a Configuration Option; This will set an arbitary configuration
          option. The syntax is -o Foo::Bar=bar.

FILES
       /etc/apt/sources.list
          Locations to fetch packages from. Configuration Item:
          Dir::Etc::SourceList.

       /etc/apt/apt.conf
          APT configuration file. Configuration Item: Dir::Etc::Main.

       /etc/apt/apt.conf.d/
          APT configuration file fragments Configuration Item:
          Dir::Etc::Parts.

       /etc/apt/preferences
          Version preferences file. This is where you would specify "pinning",
          i.e. a preference to get certain packages from a separate source or
          from a different version of a distribution. Configuration Item:
          Dir::Etc::Preferences.

       /var/cache/apt/archives/
          Storage area for retrieved package files. Configuration Item:
          Dir::Cache::Archives.

       /var/cache/apt/archives/partial/
          Storage area for package files in transit. Configuration Item:
          Dir::Cache::Archives (implicit partial).

       /var/lib/apt/lists/
          Storage area for state information for each package resource
          specified in sources.list(5) Configuration Item: Dir::State::Lists.

       /var/lib/apt/lists/partial/
          Storage area for state information in transit. Configuration Item:
          Dir::State::Lists (implicit partial).

SEE ALSO
       apt-cache(8 ), apt-cdrom(8 ), dpkg(8 ), dselect(8 ), sources.list(5),
       apt.conf(5), apt-config(8 ), apt-secure(8 ), The APT User's guide in
       /usr/share/doc/apt-doc/, apt_preferences(5), the APT Howto.

DIAGNOSTICS
       apt-get returns zero on normal operation, decimal 100 on error.

BUGS
       [1]APT bug page. If you wish to report a bug in APT, please see
       /usr/share/doc/debian/bug-reporting.txt or the reportbug(1) command.

AUTHORS
       Jason Gunthorpe
          Author.

       APT team
          Author.

REFERENCES
       1. APT bug page
          [http://bugs.debian.org/src:apt](http://bugs.debian.org/src:apt)



Linux                          29 February 2004                     APT-GET(8 )


---

