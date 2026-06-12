---
title: "Adding users problem"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by D_frag on 2006-10-07
I added users using teh useradd command and by default they should be stored under /home/username
Well i can't find the users and whats wierd is that when i check the passwd file i see that their home directories are set ?? i am using ubuntu 64bit edition if it will help

---

### Post by ewl1217 on 2006-10-07
Have you tried logging in as those users? They home directories might not be created until the first login.

---

### Post by D_frag on 2006-10-07
No i havent  , but on other distributions ex; red hat once the user is created the home directory is created .. is there any config file to alter inorder to make the directories exist once the user is added without logging off and logging in again !

---

### Post by taurus on 2006-10-07
> **D_frag said:**
> I added users using teh useradd command and by default they should be stored under /home/username
Well i can't find the users and whats wierd is that when i check the passwd file i see that their home directories are set ?? i am using ubuntu 64bit edition if it will help

Exactly what did you type to add a new user???

---

### Post by jordanmthomas on 2006-10-07
```
sudo passwd *username*
```
Did you set a password for the users?  Also, they need to be a member of the group users.

---

### Post by D_frag on 2006-10-07
i used useradd "username"
and i checked by default the users are in group 100 i.e users
and yes i did set passwords for the users

---

### Post by jordanmthomas on 2006-10-07
This is kind of cheating, but you could use the GUI tools to do it.
System --> Administration --> Users and Groups

You can set user's home directories in there.

---

### Post by taurus on 2006-10-07
From "man useradd"

> 
USERADD(8)                                                          USERADD(8)

NAME
       useradd - Create a new user or update default new user information

SYNOPSIS
       useradd [options] LOGIN

       useradd -D

       useradd -D [options]

DESCRIPTION
       When invoked without the -D option, the useradd command creates a new
       user account using the values specified on the command line and the
       default values from the system. Depending on command line options, the
       useradd command will update system files and may also create the new
       user’s home directory and copy initial files.

OPTIONS
       The options which apply to the useradd command are:

       -c, --comment COMMENT
              Any text string. It is generally a short description of the
              login, and is currently used as the field for the user’s full
              name.

       -b, --base-dir BASE_DIR
              The default base directory for the system if -d dir is not
              specified.  BASE_DIR is concatenated with the account name to
              define the home directory. If the -m option is not used,
              base_dir must exist.

       -d, --home HOME_DIR
              The new user will be created using HOME_DIR as the value for the
              user’s login directory. The default is to append the LOGIN name
              to BASE_DIR and use that as the login directory name.

       -e, --expiredate EXPIRE_DATE
              The date on which the user account will be disabled. The date is
              specified in the format YYYY-MM-DD.

       -f, --inactive INACTIVE
              The number of days after a password expires until the account is
              permanently disabled. A value of 0 disables the account as soon
              as the password has expired, and a value of -1 disables the
              feature. The default value is -1.

       -g, --gid GROUP
              The group name or number of the user’s initial login group. The
              group name must exist. A group number must refer to an already
              existing group. The default group number is 1 or whatever is
              specified in /etc/default/useradd.

       -G, --groups GROUP1[,GROUP2,...[,GROUPN]]]
              A list of supplementary groups which the user is also a member
              of. Each group is separated from the next by a comma, with no
              intervening whitespace. The groups are subject to the same
              restrictions as the group given with the -g option. The default
              is for the user to belong only to the initial group.

       -h, --help
              Display help message and exit.

       -m, --create-home
              The user’s home directory will be created if it does not exist.
              The files contained in SKEL_DIR will be copied to the home
              directory if the -k option is used, otherwise the files
              contained in /etc/skel will be used instead. Any directories
.....


So, run it with

```
sudo useradd -m <username>
```

---

### Post by D_frag on 2006-10-07
ok i've got it now .. but i saw some tutorials where u dont have to add the -m option and the directory is there ..is it possible that the tutor has edited a config file inorder to have an alias for useradd to be useradd - m ..and what would be that file

---

### Post by jordanmthomas on 2006-10-07
It's possible, but they would probably tell you they had done that.  It *could* be that they have a different version of adduser

When I set aliases, I do it in ```
~/.bashrc
```
By default, there are some examples of how to set up aliases in the file.

---

