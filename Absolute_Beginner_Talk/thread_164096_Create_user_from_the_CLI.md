---
title: "Create user from the CLI"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by zerhacke on 2006-04-22
What commands do I use to create a user from the CLI?  What are all the switches?

---

### Post by ycng76 on 2006-04-22
you can use the useradd command. E.g.  useradd -m user1
The above command will create the user called user1 and its home home directory which is /home/user1.

For other switches, refer to man pages by running "man useradd".

good luck!

---

### Post by zaba on 2006-04-23
I hope this isn't belaboring the obvious, but you will have to put sudo before that command or run it as root...

---

### Post by Sutekh on 2006-04-23
Better to use the debian specific **adduser**

```
sudo adduser <username>
```

---

### Post by zerhacke on 2006-04-23
[QUOTE=ycng76]you can use the useradd command. E.g.  useradd -m user1

For other switches, refer to man pages by running "man useradd".[/QUOTE]
man useradd didn't show anything about an -m switch.

---

### Post by gr0kzer0 on 2006-04-23
-m The user's home directory will be created for him, if it does not exist
(from useradd man page)

---

### Post by aysiu on 2006-04-23
```
USERADD(8)                                                                                                                                                                                                                               USERADD(8)

NAME
       useradd - Create a new user or update default new user information

SYNOPSIS
       useradd [options] LOGIN

       useradd -D

       useradd -D [options]

DESCRIPTION
       When invoked without the -D option, the useradd command creates a new user account using the values specified on the command line and the default values from the system. Depending on command line options, the useradd command will update
       system files and may also create the new user’s home directory and copy initial files.

OPTIONS
       The options which apply to the useradd command are:

       -c, --comment COMMENT
              Any text string. It is generally a short description of the login, and is currently used as the field for the user’s full name.

       -b, --base-dir BASE_DIR
              The default base directory for the system if -d dir is not specified.  BASE_DIR is concatenated with the account name to define the home directory. If the -m option is not used, base_dir must exist.

       -d, --home HOME_DIR
              The new user will be created using HOME_DIR as the value for the user’s login directory. The default is to append the LOGIN name to BASE_DIR and use that as the login directory name.

       -e, --expiredate EXPIRE_DATE
              The date on which the user account will be disabled. The date is specified in the format YYYY-MM-DD.

       -f, --inactive INACTIVE
              The number of days after a password expires until the account is permanently disabled. A value of 0 disables the account as soon as the password has expired, and a value of -1 disables the feature. The default value is -1.

       -g, --gid GROUP
              The group name or number of the user’s initial login group. The group name must exist. A group number must refer to an already existing group. The default group number is 1 or whatever is specified in /etc/default/useradd.

       -G, --groups GROUP1[,GROUP2,...[,GROUPN]]]
              A list of supplementary groups which the user is also a member of. Each group is separated from the next by a comma, with no intervening whitespace. The groups are subject to the same restrictions as the group given with the -g
              option. The default is for the user to belong only to the initial group.

       -h, --help
              Display help message and exit.
[b]
       -m, --create-home
              The user’s home directory will be created if it does not exist. The files contained in SKEL_DIR will be copied to the home directory if the -k option is used, otherwise the files contained in /etc/skel will be used instead. Any
              directories contained in SKEL_DIR or /etc/skel will be created in the user’s home directory as well. The -k option is only valid in conjunction with the -m option. The default is to not create the directory and to not copy any
              files.
[/b]
       -K, --key KEY=VALUE
              Overrides /etc/login.defs defaults (UID_MIN, UID_MAX, UMASK, PASS_MAX_DAYS and others).

              Example: -K PASS_MAX_DAYS=-1 can be used when creating system account to turn off password ageing, even though system account has no password at all. Multiple -K options can be specified, e.g.: -K UID_MIN=100 -K UID_MAX=499

              Note: -K UID_MIN=10,UID_MAX=499 doesn’t work yet.

       -o, --non-unique
              Allow create user account with duplicate (non-unique) UID.

       -p, --password PASSWORD
              The encrypted password, as returned by crypt(3). The default is to disable the account.

       -s, --shell SHELL
              The name of the user’s login shell. The default is to leave this field blank, which causes the system to select the default login shell.

       -u, --uid UID
              The numerical value of the user’s ID. This value must be unique, unless the -o option is used. The value must be non-negative. The default is to use the smallest ID value greater than 999 and greater than every other user. Values
              between 0 and 999 are typically reserved for system accounts.

   Changing the default values
       When invoked with the -D option, useradd will either display the current default values, or update the default values from the command line. The valid options are

       -b HOME_DIR
              The initial path prefix for a new user’s home directory. The user’s name will be affixed to the end of HOME_DIR to create the new directory name if the -d option is not used when creating a new account.
```

---

### Post by dmizer on 2006-05-27
okay ... i've looked and everywhere it says "for more information refer to man usermod" ... which i have done.  but how do i set a password for a specific user?

by reading the man (which has no concrete examples in it), and accordingly i have tried:
```
$ sudo usermod -p newuser
usage: usermod  [-u uid [-o]] [-g group] [-G group,...]
                [-d home [-m]] [-s shell] [-c comment] [-l new_name]
                [-f inactive] [-e expire ] [-p passwd] [-L|-U] name
```
```
$ sudo usermod newuser -p newpass
usermod: user newpass does not exist
```
```
~$ sudo usermod -u newuser -p newpass
usermod: user newpass does not exist
```
how the heck are the syntax on these things suppose to look?

---

### Post by Sutekh on 2006-05-27
How about```
sudo passwd <user name>
```

---

### Post by dmizer on 2006-05-27
thank you kindly (as i kick myself for not realizing it earlier). :rolleyes:

---

### Post by Sutekh on 2006-05-27
NP!!

The usermod man page was too confusing for me too

---

