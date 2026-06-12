---
title: "Sudo difference"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2006-05-07
Greetings,

Can some of you clear up a confusion i have about sudo?

there seem to be a variety of suffixes to the sudo command. There is the sudo su there is sudo -i which i usually use. I know there is sudo -s

Do they all do the same thing or what's the point?

much obliged,
--
sophtpaw

---

### Post by Sef on 2006-05-07
Here is link as to why it is better to use sudo than root.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by mostwanted on 2006-05-07
[QUOTE=sophtpaw]Greetings,

Can some of you clear up a confusion i have about sudo?

there seem to be a variety of suffixes to the sudo command. There is the sudo su there is sudo -i which i usually use. I know there is sudo -s

Do they all do the same thing or what's the point?

much obliged,
--
sophtpaw[/QUOTE]

"sudo su" runs the su command with super-user privileges. For the others, type

```
man sudo
```

The man command displays the manual files for a specific command/app. Manual files usually says what the different suffixes mean.

---

### Post by sophtpaw on 2006-05-07
[QUOTE=Sef]Here is link as to why it is better to use sudo than root.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)[/QUOTE]

Thanks for the link Sef,

but it is the different variations of sudo i'm really after. Aguess, i'll have to man sudo and see if i can understand what comes back.

I usually use sudo rather than root, but sometimes for long or specific things it is easier to have the cli set in root. Particularly, i have a friend who is a linux trouble shooter who comes over and helps out sometimes and he is used to the traditional 'su' command and doesn't want to use sudo as a prefix all the time or ask me for passwords again and again, so then again it is easier. Its out of that situation that the question has arisen. To sudo -s or sudo -i. Seemed like they all did the same thing; ie convert the cli into root

--
sophtpaw

---

### Post by mostwanted on 2006-05-07
> **sophtpaw]Thanks for the link Sef,

but it is the different variations of sudo i'm really after. Aguess, i'll have to man sudo and see if i can understand what comes back.

I usually use sudo rather than root, but sometimes for long or specific things it is easier to have the cli set in root. Particularly, i have a friend who is a linux trouble shooter who comes over and helps out sometimes and he is used to the traditional 'su' command and doesn't want to use sudo as a prefix all the time or ask me for passwords again and again, so then again it is easier. Its out of that situation that the question has arisen. To sudo -s or sudo -i. Seemed like they all did the same thing said:**
> 


Okay, I'll try to be more clear. When you type in letters behind a "-" in a command or words behind a "--" then you add command-line options. The program/command interprets these options and behaves differently when you supply them with these options.  From the man file:

[QUOTE]OPTIONS
       sudo accepts the following command line options:

       -H  The -H (HOME) option sets the HOME environment variable to the
           homedir of the target user (root by default) as specified in
           passwd(5).  By default, sudo does not modify HOME (see set_home and
           always_set_home in sudoers(5)).

       -K  The -K (sure kill) option is like -k except that it removes the
           user’s timestamp entirely.  Like -k, this option does not require a
           password.

       -L  The -L (list defaults) option will list out the parameters that may
           be set in a Defaults line along with a short description for each.
           This option is useful in conjunction with grep(1).

       -P  The -P (preserve group vector) option causes sudo to preserve the
           invoking user’s group vector unaltered.  By default, sudo will ini&#8208;
           tialize the group vector to the list of groups the target user is
           in.  The real and effective group IDs, however, are still set to
           match the target user.

       -S  The -S (stdin) option causes sudo to read the password from the
           standard input instead of the terminal device.

       -V  The -V (version) option causes sudo to print the version number and
           exit.  If the invoking user is already root the -V option will
           print out a list of the defaults sudo was compiled with as well as
           the machine’s local network addresses.

       -a  The -a (authentication type) option causes sudo to use the speci&#8208;
           fied authentication type when validating the user, as allowed by
           /etc/login.conf.  The system administrator may specify a list of
           sudo-specific authentication methods by adding an "auth-sudo" entry
           in /etc/login.conf.  This option is only available on systems that
           support BSD authentication where sudo has been configured with the
           --with-bsdauth option.

       -b  The -b (background) option tells sudo to run the given command in
           the background.  Note that if you use the -b option you cannot use
           shell job control to manipulate the process.

       -c  The -c (class) option causes sudo to run the specified command with
           resources limited by the specified login class.  The class argument
           can be either a class name as defined in /etc/login.conf, or a sin&#8208;
           gle ’-’ character.  Specifying a class of - indicates that the com&#8208;
           mand should be run restricted by the default login capabilities for
           the user the command is run as.  If the class argument specifies an
           existing user class, the command must be run as root, or the sudo
           command must be run from a shell that is already root.  This option
           is only available on systems with BSD login classes where sudo has
           been configured with the --with-logincap option.

The -e (edit) option indicates that, instead of running a command,
           the user wishes to edit one or more files.  In lieu of a command,
           the string "sudoedit" is used when consulting the sudoers file.  If
           the user is authorized by sudoers the following steps are taken:

           1.      Temporary copies are made of the files to be edited with
                   the owner set to the invoking user.

           2.      The editor specified by the VISUAL or EDITOR environment
                   variables is run to edit the temporary files.  If neither
                   VISUAL nor EDITOR are set, the program listed in the editor
                   sudoers variable is used.

           3.      If they have been modified, the temporary files are copied
                   back to their original location and the temporary versions
                   are removed.

           If the specified file does not exist, it will be created.  Note
           that unlike most commands run by sudo, the editor is run with the
           invoking user’s environment unmodified.  If, for some reason, sudo
           is unable to update a file with its edited version, the user will
           receive a warning and the edited copy will remain in a temporary
           file.

       -h  The -h (help) option causes sudo to print a usage message and exit.

       -i  The -i (simulate initial login) option runs the shell specified in
           the passwd(5) entry of the user that the command is being run as.
           The command name argument given to the shell begins with a - to
           tell the shell to run as a login shell.  sudo attempts to change to
           that user’s home directory before running the shell.  It also ini&#8208;
           tializes the environment, leaving TERM unchanged, setting HOME,
           SHELL, USER, LOGNAME, and PATH, and unsetting all other environment
           variables.  Note that because the shell to use is determined before
           the sudoers file is parsed, a runas_default setting in sudoers will
           specify the user to run the shell as but will not affect which
           shell is actually run.

       -k  The -k (kill) option to sudo invalidates the user’s timestamp by
           setting the time on it to the epoch.  The next time sudo is run a
           password will be required.  This option does not require a password
           and was added to allow a user to revoke sudo permissions from a
           .logout file.

       -l  The -l (list) option will list out the allowed (and forbidden) com&#8208;
           mands for the user on the current host.

       -p  The -p (prompt) option allows you to override the default password
           prompt and use a custom one.  The following percent (‘%’) escapes
           are supported:

           %u      expanded to the invoking user’s login name

           %U      expanded to the login name of the user the command will be
                   run as (defaults to root)

           %h      expanded to the local hostname without the domain name

           %H      expanded to the local hostname including the domain name
                   (on if the machine’s hostname is fully qualified or the
                   fqdn sudoers option is set)

           %%      two consecutive % characters are collapsed into a single %
                   character

       -s  The -s (shell) option runs the shell specified by the SHELL envi&#8208;
           ronment variable if it is set or the shell as specified in
           passwd(5).

       -u  The -u (user) option causes sudo to run the specified command as a
           user other than root.  To specify a uid instead of a username, use
           #uid.  Note that if the targetpw Defaults option is set (see sudo&#8208;
           ers(5)) it is not possible to run commands with a uid not listed in
           the password database.

       -v  If given the -v (validate) option, sudo will update the user’s
           timestamp, prompting for the user’s password if necessary.  This
           extends the sudo timeout for another 15 minutes (or whatever the
           timeout is set to in sudoers) but does not run a command.

       --  The -- flag indicates that sudo should stop processing command line
           arguments.  It is most useful in conjunction with the -s flag.

You want the parts about -i and -s specifically.

---

