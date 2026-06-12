---
title: "sudo and root password"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by B-Con on 2007-03-17
I have a couple questions related to root permissions. 

First, the concept of "sudo". I've been reading on the "sudo" command, but I have to admit that I still don't get exactly how it works. Basically, how is it possible that I'm executing root comments via "sudo" when I'm only supplying *my* account's password? Like, if a file is owned by root, how is it possible that I can use the "sudo" comment to change ownership of the file by only using my own password? Or if I run "sudo su" and login as root using my own passowrd. Doesn't that kind of nullify the concept of a root account password if I can act as root using my own passord?

Also, Ubuntu comes without a default root password. Does this mean that the root password is blank, or does it mean that root is "deactivated", so to speak? If it were just blank, then I would think you could log in as root without needing a password, which I can't do. 

Sorry for the seemingly elementary questions, I just honestly can't rationalize how this works.

---

### Post by Kateikyoushi on 2007-03-17
As far as I know there is a (maybe random) root password what we do not know, that is why you can't login, of course you can change it and are able to login as root, but the devs do not want it.

Think of your user password that it has 2 functions to login, and to become root temporarily.

What difference does it make whether you use your login password or another to become root ? This design is easier for new users to use and less dangerous than using root.

---

### Post by Space Cowboy on 2007-03-17
It is not blank, theres just not a password enabled for it, you have to manually do that, I did that one time while I was impatient and didn't want to keep typing in sudo and passwords for things like synaptic and networking, but I don't log in as root most of the time.

---

### Post by B-Con on 2007-03-17
Shouldn't root access be restricted by the root password, though? If sudo can get root access without the password, why couldn't something else? What makes root secure if it's not protected by it's own password?

---

### Post by aysiu on 2007-03-17
Think of it like your bank ATM card.

You have the card. No one else has that card.

But even if you have that card, you have to enter *your* password to gain access to the money in your bank account.

The computer is your computer but "root" (i.e., the bank) owns all the system files. If you enter your password (PIN), you can have temporary access to those files (money).

---

### Post by freebird54 on 2007-03-18
If you are worried about the security aspects - you can create a new user account for you to use most of the time - that does NOT have access to **sudo**.  This will give you 2 layers to get through before you can compromise your system!

You could think of sudo as a version of **su** with a timeout - so you can't leave a root shell around by accident....

And  - if you REALLY want to do it another way, it can be set back to normal.  I recommend that you don't however, and think of it as a Vista model UAC that actually works!

---

### Post by Madpilot on 2007-03-18
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) has all the information you're looking for on how Ubuntu handles sudo/root privs, and even how to enable a 'real' root account - which is neither recommend or needed!

---

### Post by h0ax on 2007-03-18
> s**Isn't using *sudo* essentially the same as running as root?**

 This is a common misconception about *sudo* among Linux-using non-Ubuntu users. When you run as root, anything you do has system-wide privileges. You can do **anything**. You have free reign over your entire system. This would be akin to walking around with everything you own, including all your money in cash on your person. 
When you run as an *admin* in Ubuntu, you're almost always a limited user. If you preface a terminal command with the word *sudo* or preface a graphical command with *gksudo* or *kdesu*, you allow yourself (and only with password authentication) to temporarily assume root privileges for that one task. This would be like having your belongings in a safe with a combination lock or keeping all your money in a bank, where you can access your account through an ATM card and PIN code. 
 There is a fifteen-minute "timeout" for *sudo*. If you launch one command with *sudo*, you'll be prompted for a command, and within the same shell, you won't be prompted again for other *sudo* commands for the next fifteen minutes. If you want, you can [change the *sudo* timeout to something lower]("http://ubuntuforums.org/showthread.php?p=116697#post116697") so that you'll **always** be prompted for a password on every *sudo* command.  


heh

---

### Post by B-Con on 2007-03-18
Thanks for the replies thus far, but I still don't understand (even after reading the link) how sudo gains root privledges.

I'm looking at it this way: root exists as the supreme account and it is password protected. Now, sudocomes along and wants to run itself with root's privildges. How can it do that without access to root's password? In other words, how does sudo get to run with root priviledges, but not some other program? What's to keep some other program from doing exactly what sudo does and also gain root access?

Basically, I suppose I could rephrase it like this: Does the user password ascention priviledge come from sudo, or Linux itself? Does the operating system itself make the call to give root privledges to a user via sudo, or is it sudo that makes that call? If sudo makes that call, then I ask my above question. If it's the operating system itself that associates the user's password with root priviledges, then that makes more sense.

---

### Post by aysiu on 2007-03-18
It's all defined in the /etc/sudoers file.

The default file looks like this: ```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults !lecture,tty_tickets,!fqdn

# User privilege specification
root ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
``` See how it basically says that members of the *admin* group are allowed to gain root privileges? It doesn't allow **all** users to gain temporary root privileges--only those in the *admin* group. The first user you create during installation automatically belongs to the *admin* group. Any subsequently created users have to be added to the *admin* group manually (by someone else in the *admin* group).

---

### Post by B-Con on 2007-03-19
Is /etc/sudoers interpretted by the OS or the sudo program? Does the OS use the file to determine who's allowed to use sudo to escilate their priviledges, or does sudo use the file to determine that? If it's sudo that interprets the file, it's still the same problem: Where does sudo itself get permission to escilate to root? Is the OS in charge of recognizing that user X is of groupt Admin and has sufficient priviledges to run as root? If it's the OS that does the interpreting, then it makes sense, but since sudo is an addon feature and not installed by default in all installationsI doubt that's the case.

Here's how I'm guessing it works, based on what I know so far:
- User invokes sudo
- sudo checks user's credentials against /etc/sudoers
- If the user is authorized by the sudoers file, then sudo passes the user's password onto the OS
- If the user's credentials validate with the OS (password is correct and user is of group Admin), then root permission is granted

Does that sound right?

---

### Post by bodhi.zazen on 2007-03-19
You are asking a lot of good questions.

Perhaps a little of topic, but you can enable a root password if you like and then disable sudo. Or you can limit the commands available to sudo ...

I hate to say it, but with such a detailed question perhaps you would be interested in this :

[http://www.gratisoft.us/sudo/man/sudo.html](http://www.gratisoft.us/sudo/man/sudo.html)

One last thing, if you plan to do a lot of sys admin, and do not want to type sudo over and over ...

just ```
sudo -i
```

---

### Post by aysiu on 2007-03-19
Most beginners don't really ask questions on this kind of level. If you have this level of interest, you can do some more investigating by reading the manual for *sudo*: ```
SUDO(8)                      MAINTENANCE COMMANDS                      SUDO(8)



NAME
       sudo, sudoedit - execute a command as another user

SYNOPSIS
       sudo -K | -L | -V | -h | -k | -l | -v

       sudo [-HPSb] [-a auth_type] [-c class|-] [-p prompt] [-u username|#uid]
       {-e file [...] | -i | -s | command}

       sudoedit [-S] [-a auth_type] [-p prompt] [-u username|#uid] file [...]

DESCRIPTION
       sudo allows a permitted user to execute a command as the superuser or
       another user, as specified in the sudoers file.  The real and effective
       uid and gid are set to match those of the target user as specified in
       the passwd file and the group vector is initialized based on the group
       file (unless the -P option was specified).  If the invoking user is
       root or if the target user is the same as the invoking user, no pass&#8208;
       word is required.  Otherwise, sudo requires that users authenticate
       themselves with a password by default (NOTE: in the default configura&#8208;
       tion this is the user&#8217;s password, not the root password).  Once a user
       has been authenticated, a timestamp is updated and the user may then
       use sudo without a password for a short period of time (15 minutes
       unless overridden in sudoers).

       When invoked as sudoedit, the -e option (described below), is implied.

       sudo determines who is an authorized user by consulting the file
       /etc/sudoers.  By giving sudo the -v flag a user can update the time
       stamp without running a command. The password prompt itself will also
       time out if the user&#8217;s password is not entered within 0 minutes (unless
       overridden via sudoers).

       If a user who is not listed in the sudoers file tries to run a command
       via sudo, mail is sent to the proper authorities, as defined at config&#8208;
       ure time or in the sudoers file (defaults to root).  Note that the mail
       will not be sent if an unauthorized user tries to run sudo with the -l
       or -v flags.  This allows users to determine for themselves whether or
       not they are allowed to use sudo.

       If sudo is run by root and the SUDO_USER environment variable is set,
       sudo will use this value to determine who the actual user is.  This can
       be used by a user to log commands through sudo even when a root shell
       has been invoked.  It also allows the -e flag to remain useful even
       when being run via a sudo-run script or program.  Note however, that
       the sudoers lookup is still done for root, not the user specified by
       SUDO_USER.

       sudo can log both successful and unsuccessful attempts (as well as
       errors) to syslog(3), a log file, or both.  By default sudo will log
       via syslog(3) but this is changeable at configure time or via the sudo&#8208;
       ers file.

OPTIONS
       sudo accepts the following command line options:

       -H  The -H (HOME) option sets the HOME environment variable to the
           homedir of the target user (root by default) as specified in
           passwd(5).  By default, sudo does not modify HOME (see set_home and
           always_set_home in sudoers(5)).

       -K  The -K (sure kill) option is like -k except that it removes the
           user&#8217;s timestamp entirely.  Like -k, this option does not require a
           password.

       -L  The -L (list defaults) option will list out the parameters that may
           be set in a Defaults line along with a short description for each.
           This option is useful in conjunction with grep(1).

       -P  The -P (preserve group vector) option causes sudo to preserve the
           invoking user&#8217;s group vector unaltered.  By default, sudo will ini&#8208;
           tialize the group vector to the list of groups the target user is
           in.  The real and effective group IDs, however, are still set to
           match the target user.

       -S  The -S (stdin) option causes sudo to read the password from the
           standard input instead of the terminal device.

       -V  The -V (version) option causes sudo to print the version number and
           exit.  If the invoking user is already root the -V option will
           print out a list of the defaults sudo was compiled with as well as
           the machine&#8217;s local network addresses.

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
           gle &#8217;-&#8217; character.  Specifying a class of - indicates that the com&#8208;
           mand should be run restricted by the default login capabilities for
           the user the command is run as.  If the class argument specifies an
           existing user class, the command must be run as root, or the sudo
           command must be run from a shell that is already root.  This option
           is only available on systems with BSD login classes where sudo has
           been configured with the --with-logincap option.

       -e  The -e (edit) option indicates that, instead of running a command,
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
           invoking user&#8217;s environment unmodified.  If, for some reason, sudo
           is unable to update a file with its edited version, the user will
           receive a warning and the edited copy will remain in a temporary
           file.

       -h  The -h (help) option causes sudo to print a usage message and exit.

       -i  The -i (simulate initial login) option runs the shell specified in
           the passwd(5) entry of the user that the command is being run as.
           The command name argument given to the shell begins with a - to
           tell the shell to run as a login shell.  sudo attempts to change to
           that user&#8217;s home directory before running the shell.  It also ini&#8208;
           tializes the environment, leaving TERM unchanged, setting HOME,
           SHELL, USER, LOGNAME, and PATH, and unsetting all other environment
           variables.  Note that because the shell to use is determined before
           the sudoers file is parsed, a runas_default setting in sudoers will
           specify the user to run the shell as but will not affect which
           shell is actually run.

       -k  The -k (kill) option to sudo invalidates the user&#8217;s timestamp by
           setting the time on it to the epoch.  The next time sudo is run a
           password will be required.  This option does not require a password
           and was added to allow a user to revoke sudo permissions from a
           .logout file.

       -l  The -l (list) option will list out the allowed (and forbidden) com&#8208;
           mands for the user on the current host.

       -p  The -p (prompt) option allows you to override the default password
           prompt and use a custom one.  The following percent (&#8216;%&#8217;) escapes
           are supported:

           %u      expanded to the invoking user&#8217;s login name

           %U      expanded to the login name of the user the command will be
                   run as (defaults to root)

           %h      expanded to the local hostname without the domain name

           %H      expanded to the local hostname including the domain name
                   (on if the machine&#8217;s hostname is fully qualified or the
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

       -v  If given the -v (validate) option, sudo will update the user&#8217;s
           timestamp, prompting for the user&#8217;s password if necessary.  This
           extends the sudo timeout for another 15 minutes (or whatever the
           timeout is set to in sudoers) but does not run a command.

       --  The -- flag indicates that sudo should stop processing command line
           arguments.  It is most useful in conjunction with the -s flag.

RETURN VALUES
       Upon successful execution of a program, the return value from sudo will
       simply be the return value of the program that was executed.

       Otherwise, sudo quits with an exit value of 1 if there is a configura&#8208;
       tion/permission problem or if sudo cannot execute the given command.
       In the latter case the error string is printed to stderr.  If sudo can&#8208;
       not stat(2) one or more entries in the user&#8217;s PATH an error is printed
       on stderr.  (If the directory does not exist or if it is not really a
       directory, the entry is ignored and no error is printed.)  This should
       not happen under normal circumstances.  The most common reason for
       stat(2) to return "permission denied" is if you are running an auto&#8208;
       mounter and one of the directories in your PATH is on a machine that is
       currently unreachable.

SECURITY NOTES
       sudo tries to be safe when executing external commands.  Variables that
       control how dynamic loading and binding is done can be used to subvert
       the program that sudo runs.  To combat this the LD_*, _RLD_*,
       SHLIB_PATH (HP-UX only), and LIBPATH (AIX only) environment variables
       are removed from the environment passed on to all commands executed.
       sudo will also remove the IFS, CDPATH, ENV, BASH_ENV, KRB_CONF, KRB&#8208;
       CONFDIR, KRBTKFILE, KRB5_CONFIG, LOCALDOMAIN, RES_OPTIONS, HOSTALIASES,
       NLSPATH, PATH_LOCALE, TERMINFO, TERMINFO_DIRS and TERMPATH variables as
       they too can pose a threat.  If the TERMCAP variable is set and is a
       pathname, it too is ignored.  Additionally, if the LC_* or LANGUAGE
       variables contain the / or % characters, they are ignored.  Environment
       variables with a value beginning with () are also removed as they could
       be interpreted as bash functions.  If sudo has been compiled with
       SecurID support, the VAR_ACE, USR_ACE and DLC_ACE variables are cleared
       as well.  The list of environment variables that sudo clears is con&#8208;
       tained in the output of sudo -V when run as root.

       To prevent command spoofing, sudo checks "." and "" (both denoting cur&#8208;
       rent directory) last when searching for a command in the user&#8217;s PATH
       (if one or both are in the PATH).  Note, however, that the PATH envi&#8208;
       ronment variable is further modified in Debian because of the use of
       the SECURE_PATH build option.

       For security reasons, if your OS supports shared libraries and does not
       disable user-defined library search paths for setuid programs (most
       do), you should either use a linker option that disables this behavior
       or link sudo statically.

       sudo will check the ownership of its timestamp directory (/var/run/sudo
       by default) and ignore the directory&#8217;s contents if it is not owned by
       root and only writable by root.  On systems that allow non-root users
       to give away files via chown(2), if the timestamp directory is located
       in a directory writable by anyone (e.g.: /tmp), it is possible for a
       user to create the timestamp directory before sudo is run.  However,
       because sudo checks the ownership and mode of the directory and its
       contents, the only damage that can be done is to "hide" files by
       putting them in the timestamp dir.  This is unlikely to happen since
       once the timestamp dir is owned by root and inaccessible by any other
       user the user placing files there would be unable to get them back out.
       To get around this issue you can use a directory that is not world-
       writable for the timestamps (/var/adm/sudo for instance) or create
       /var/run/sudo with the appropriate owner (root) and permissions (0700)
       in the system startup files.

       sudo will not honor timestamps set far in the future.  Timestamps with
       a date greater than current_time + 2 * TIMEOUT will be ignored and sudo
       will log and complain.  This is done to keep a user from creating
       his/her own timestamp with a bogus date on systems that allow users to
       give away files.

       Please note that sudo will only log the command it explicitly runs.  If
       a user runs a command such as sudo su or sudo sh, subsequent commands
       run from that shell will not be logged, nor will sudo&#8217;s access control
       affect them.  The same is true for commands that offer shell escapes
       (including most editors).  Because of this, care must be taken when
       giving users access to commands via sudo to verify that the command
       does not inadvertently give the user an effective root shell.

ENVIRONMENT
       sudo utilizes the following environment variables:

        EDITOR                 Default editor to use in -e (sudoedit) mode if
                               VISUAL is not set

        HOME                   In -s or -H mode (or if sudo was configured with
                               the --enable-shell-sets-home option), set to
                               homedir of the target user

        PATH                   Set to a sane value if sudo was configured with
                               the --with-secure-path option (true for Debian)

        SHELL                  Used to determine shell to run with -s option

        SUDO_PROMPT            Used as the default password prompt

        SUDO_COMMAND           Set to the command run by sudo

        SUDO_USER              Set to the login of the user who invoked sudo

        SUDO_UID               Set to the uid of the user who invoked sudo

        SUDO_GID               Set to the gid of the user who invoked sudo

        SUDO_PS1               If set, PS1 will be set to its value

        USER                   Set to the target user (root unless the -u option
                               is specified)

        VISUAL                 Default editor to use in -e (sudoedit) mode

FILES
        /etc/sudoers           List of who can run what
        /var/run/sudo              Directory containing timestamps

EXAMPLES
       Note: the following examples assume suitable sudoers(5) entries.

       To get a file listing of an unreadable directory:

        $ sudo ls /usr/local/protected

       To list the home directory of user yazza on a machine where the file
       system holding ~yazza is not exported as root:

        $ sudo -u yazza ls ~yazza

       To edit the index.html file as user www:

        $ sudo -u www vi ~www/htdocs/index.html

       To shutdown a machine:

        $ sudo shutdown -r +15 "quick reboot"

       To make a usage listing of the directories in the /home partition.
       Note that this runs the commands in a sub-shell to make the cd and file
       redirection work.

        $ sudo sh -c "cd /home ; du -s * | sort -rn > USAGE"

SEE ALSO
       grep(1), su(1), stat(2), login_cap(3), sudoers(5), passwd(5), visudo(8)

       The file /usr/share/doc/sudo/OPTIONS describes the options used for
       building the Debian version of sudo, some of which change default
       behaviors documented elsewhere in this document.

AUTHORS
       Many people have worked on sudo over the years; this version consists
       of code written primarily by:

               Todd Miller
               Chris Jepeway

       See the HISTORY file in the sudo distribution or visit
       http://www.sudo.ws/sudo/history.html for a short history of sudo.

CAVEATS
       There is no easy way to prevent a user from gaining a root shell if
       that user is allowed to run arbitrary commands via sudo.  Also, many
       programs (such as editors) allow the user to run commands via shell
       escapes, thus avoiding sudo&#8217;s checks.  However, on most systems it is
       possible to prevent shell escapes with sudo&#8217;s noexec functionality.
       See the sudoers(5) manual for details.

       It is not meaningful to run the cd command directly via sudo, e.g.

        $ sudo cd /usr/local/protected

       since when whe command exits the parent process (your shell) will still
       be the same.  Please see the EXAMPLES section for more information.

       If users have sudo ALL there is nothing to prevent them from creating
       their own program that gives them a root shell regardless of any &#8217;!&#8217;
       elements in the user specification.

       Running shell scripts via sudo can expose the same kernel bugs that
       make setuid shell scripts unsafe on some operating systems (if your OS
       has a /dev/fd/ directory, setuid shell scripts are generally safe).

BUGS
       If you feel you have found a bug in sudo, please submit a bug report at
       http://www.sudo.ws/sudo/bugs/

SUPPORT
       Commercial support is available for sudo, see
       http://www.sudo.ws/sudo/support.html for details.

       Limited free support is available via the sudo-users mailing list, see
       http://www.sudo.ws/mailman/listinfo/sudo-users to subscribe or search
       the archives.

DISCLAIMER
       Sudo is provided &#8216;&#8216;AS IS&#8217;&#8217; and any express or implied warranties,
       including, but not limited to, the implied warranties of merchantabil&#8208;
       ity and fitness for a particular purpose are disclaimed.  See the
       LICENSE file distributed with sudo or
       http://www.sudo.ws/sudo/license.html for complete details.



1.6.8p12                         Juli 17, 2006                         SUDO(8)
``` You should also note [that *sudo* is an actual package installed on Ubuntu](http://packages.ubuntu.com/edgy/admin/sudo). It is a part of the system.

---

### Post by FallNAngel on 2007-03-21
I think the "issue" B-Con has is the same as mine.  First a little background..

I got started in Linux years ago, used it exclusively for about a year and went back to Windows (for gaming).  Now, I'm looking to get back into Linux.  I'm not a newbie to Linux and I'm full aware of what can be done with root permissions, and why you shouldn't run the system under the root account, but instead use it only when necessary.

Now, say I'm in Slackware (or pretty much any other distro) and want to run something as root.  Generally, I just open a terminal, type "su" or "su -c <command>", type in the root password and off I go.  The times that I need to run as root exclusively are few and far between.  The problem I have with Ubuntu isn't that I get prompted for a password, but that it'll cache the password and that it's that it's prompting me for *my* password.  If I'm already logged in, it doesn't seem any more secure.  For instance, if I walk away from the computer for a moment or forget to lock it, someone can open a terminal, type "passwd", reset my password and start running whatever they want.  Problem is, if I remove the sudo privilage, half of the System menu's are pointless, as they all want to run under sudo... which doesn't work. 

So far, my only complaint about Ubuntu is that it prompts me for *my* password, instead of a "root" password and the fact that it'll cache it.  The last thing I want is for the system to cache my password because I ran synaptic, then let me do something stupid because the password was cached.  If there was a way to configure the install to enable the root account with a root password, add a normal user and have administrative stuff just ask for the root password, I personally think thing's would be much better.  The people who don't care will just give both users the same password and everything's transparent to them (it'll function just as it is now).  For those who want things a bit more secure, we can have that too.

Just my $0.02

*edit*
after reading a bit more into the sudoers file, it appears this is possible.

looking into the rootpw option will prompt for the root password (not the users) and there's an option -K that can be used with the sudo command to not cache the password (not sure if there's an option for sudoers).  I'll post back with what I find.

---

### Post by aysiu on 2007-03-21
> **FallNAngel said:**
> 
For instance, if I walk away from the computer for a moment or forget to lock it, someone can open a terminal, type "passwd", reset my password and start running whatever they want. If you walk away from your computer, try locking it. You can easily set up a keyboard shortcut for locking the screen. If you're away from it for a long time and don't trust your friends and family members, well, you're screwed. Physical access is root access. If people who have physical access to your computer have only a little know-how and a lot of time, they own your computer--root, user, everything.

> The last thing I want is for the system to cache my password because I ran synaptic, then let me do something stupid because the password was cached. You can get rid of the 15-minute timeout by following [these instructions](http://ubuntuforums.org/showthread.php?p=116697#post116697).

---

### Post by steve.horsley on 2007-03-21
Two straight answers to two straight questions:

sudo is able to run programs under a different user id because the sudo executable itself is a **setuid root** executable. See the s in this output:
> steve@Dingly:~$ ls -l /usr/bin/sudo
-rwsr-xr-x 2 root root 91508 2006-10-09 12:37 /usr/bin/sudo

This means that regardless of who launches the sudo executable, it actually runs with root's identity. Since sudo is running as root, it has the right to launch other processes with whatever user id it chooses. This executable is of course trusted to behave itself, and only to do things that are permitted in the /etc/sudoers config file. 

Passwords for users are stored in an encrypted form in the file /etc/shadow. Locked accounts have a special character in the place of the encrypted password - no possible password can create a single character encrypted string, so this renders it impossible for the user to log in. See **man shadow** for more info. However, it is still possible for root (or setuid programs) to change their id to this account and then function normally as that user - it's the password that's locked out, that's all.

---

### Post by B-Con on 2007-03-23
Ah, very nice explanation. Thanks. :)

---

### Post by ac7ss on 2007-03-24
I understand the risk of running as root. but tire of password entry for things like network configuration.

Is there safety in the following?

create a group called wifi
add yourself to that group.

chgrp wifi /sbin/iwconfig
chmod o-x /sbin/iwconfig
chmod u+s /sbin/iwconfig

granted, you must be root to do this.

---

### Post by aysiu on 2007-03-24
> **ac7ss said:**
> I understand the risk of running as root. but tire of password entry for things like network configuration. Then do as bodhi.zazen suggested: ```
sudo -i
``` This will essentially be the same as a root login.

---

### Post by ac7ss on 2007-03-26
But the question was: is the setuid a good solution?

I would rather not be doing things as root. (I formerly used the sudu command to handle the script.)

---

### Post by Merick on 2007-04-01
lol, i've only been using Ubuntu for a couple of days now, and it's the first version of linux I've ever used. While trying to figure out how to change some of the protected config files to get my montior to work correctly, I almost accidentally figured something out:

sudo su

type this in, and you will be in root

---

### Post by Psychotron on 2007-04-02
Yeh thats how you do it on almost any distro but it only works if your in the group or are a user allowed in the sudoers file.  If you are not that user or in that group then it wont work.

---

### Post by B-Con on 2007-04-07
Ok, so, to summarize, I think this is a fair description of how it works:

- The binary /usr/bin/sudo has the owner user and group as root.
- However, it has permissions to allow everyone to execute it. (chmod __5 /usr/bin/sudo)
- Thus when someone executes the sudo program, it runs with root priviledges.
- When it executes, the sudo program authenticates the user and their desired action against the sudoers file
- If the user is allowed to do what they want to do, they are prompted for their password by sudo. If they enter the correct password, sudo performs the action the user requested.

I hope that summarizes it accurately.

---

### Post by bodhi.zazen on 2007-04-07
> **B-Con said:**
> Ok, so, to summarize, I think this is a fair description of how it works:

- The binary /usr/bin/sudo has the owner user and group as root.
- However, it has permissions to allow everyone to execute it. (chmod __5 /usr/bin/sudo)
- Thus when someone executes the sudo program, it runs with root priviledges.
- When it executes, the sudo program authenticates the user and their desired action against the sudoers file
- If the user is allowed to do what they want to do, they are prompted for their password by sudo. If they enter the correct password, sudo performs the action the user requested.

I hope that summarizes it accurately.

That is a nice summary. I may direct a few folks to it if I may.

always nice to see that light-bulb of understanding. Congratulations.

---

### Post by B-Con on 2007-04-10
Thanks, this question was really bugging me for a while.

Actually, on further reading, I realize I made a slight error in my above description. So as not to confuse any future readers of this thread, here's the updated version:

- The binary /usr/bin/sudo has the owner user and group as root.
- It has permissions to allow everyone to execute it. (chmod XXX5 /usr/bin/sudo)
- It also has the setuid bit set that lets the program run with the permissions of it's owner. (chmod 4XXX)
- Thus when someone executes the sudo program, it runs with the priviledges of the owner, which is root.
- When the user invokes the sudo program, it authenticates the user and their desired action against the sudoers file to see if the user is allowed to perform the action.
- If the user is allowed to do what they're trying to do, they are prompted for their password by sudo. sudo then confirms the password by using Linux's resources to check it. If they enter the correct password, sudo performs the action the user requested.

---

