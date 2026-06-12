---
title: "Weird behaviour of terminal"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by sjosh_theone on 2007-12-09
guys when i type in "sudo -i" in my terminal it show me the following:-


-l, --link                   link files instead of copying
  -L, --dereference            always follow symbolic links
  -P, --no-dereference         never follow symbolic links
  -p                           same as --preserve=mode,ownership,timestamps
      --preserve[=ATTR_LIST]   preserve the specified attributes (default:
                                 mode,ownership,timestamps), if possible
                                 additional attributes: links, all
  -c                           same as --preserve=context
      --no-preserve=ATTR_LIST  don't preserve the specified attributes
      --parents                use full source file name under DIRECTORY
  -R, -r, --recursive          copy directories recursively
      --remove-destination     remove each existing destination file before
                                 attempting to open it (contrast with --force)
      --sparse=WHEN            control creation of sparse files
      --strip-trailing-slashes remove any trailing slashes from each SOURCE
                                 argument
  -s, --symbolic-link          make symbolic links instead of copying
  -S, --suffix=SUFFIX          override the usual backup suffix
  -t, --target-directory=DIRECTORY  copy all SOURCE arguments into DIRECTORY
  -T, --no-target-directory    treat DEST as a normal file
  -u, --update                 copy only when the SOURCE file is newer
                                 than the destination file or when the
                                 destination file is missing
  -v, --verbose                explain what is being done
  -x, --one-file-system        stay on this file system
  -Z, --context=CONTEXT        set security context of copy to CONTEXT
      --help     display this help and exit
      --version  output version information and exit

By default, sparse SOURCE files are detected by a crude heuristic and the
corresponding DEST file is made sparse as well.  That is the behavior
selected by --sparse=auto.  Specify --sparse=always to create a sparse DEST
file whenever the SOURCE file contains a long enough sequence of zero bytes.
Use --sparse=never to inhibit creation of sparse files.

The backup suffix is `~', unless set with --suffix or SIMPLE_BACKUP_SUFFIX.
The version control method may be selected via the --backup option or through
the VERSION_CONTROL environment variable.  Here are the values:

  none, off       never make backups (even if --backup is given)
  numbered, t     make numbered backups
  existing, nil   numbered if numbered backups exist, simple otherwise
  simple, never   always make simple backups

As a special case, cp makes a backup of SOURCE when the force and backup
options are given and SOURCE and DEST are the same name for an existing,
regular file.

Report bugs to <bug-coreutils@gnu.org>.
#
#
[screen terminating]

If I want to exit I need to type in "exit". WHats going on ?????
Thanks in advance.

---

### Post by nikoPSK on 2007-12-09
sudo -i makes you root same as sudo su. If you want to stop being root you type exit. Example:

```
niko@home:~$ sudo -i
[sudo] password for niko:
root@home:~# 

```

That # sign means I am now root. Say i don't want to be root anymore:

```
root@home:~# exit
logout
niko@home:~$ 

```

---

### Post by PinkFloyd102489 on 2007-12-09
sudo -s does the same thing also

---

### Post by nikoPSK on 2007-12-09
yes it does. :lolflag:

---

### Post by sjosh_theone on 2007-12-12
q

---

