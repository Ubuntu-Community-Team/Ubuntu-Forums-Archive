---
title: "Password manager?"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by Lucifiel on 2007-05-05
My aim: to simply store passwords since I keep forgetting them. These include web passwords, program passwords, ftp passwords, etc. 

So, I've been digging around and ended up with Keyring manager. However, I discovered KeyRing Manager is used for automatically entering passwords into various programs, etc. Now that I don't want or need. I simply need a manager for keeping my passwords so that I can retrieve them, should I forget them.

Writing my passwords down isn't the safest route, though.

---

### Post by Tsen on 2007-05-05
If you just want to store them, why not just put them in a text file, then encrypt the or save it to an encrypted disk?  You'd have a master password for the file, and then the list just show passwords for programs/websites/accounts, whatever.

---

### Post by jpkotta on 2007-05-05
I keep my passwords in a text file and encrypt it with gpg.  I have the following script to help make sure it never leaves behind an unecrypted version.  You must set up GPG first (check the wiki).  You may want a different editor; nano is installed by default.  I would imagine that there are much nicer programs to do the same thing, but at least this way you know what is happening.

```
#!/bin/bash

# this is a script to automatically decrypt a file with gnupg, edit it, and 
# re-encrypt if there are changes.

working_dir=/home/jpkotta/doc
backup_dir=/home/jpkotta/backup
recipient=jpkotta
editor=emacs

plaintext_file=key.txt
crypt_file=${plaintext_file}.gpg
comp_file=${plaintext_file}.back

cd $working_dir

# decrypt the file
# gpg will prompt for password
if /usr/bin/gpg --output ./$plaintext_file --decrypt ./$crypt_file ; then
    echo "The file key.txt.gpg has been decrypted to $working_dir/$plaintext_file."
else
    echo "Error decrypting the file $working_dir/$crypt_file."
    exit 1
fi

# backup the file so we can see if changes were made
/bin/cp -f ./$plaintext_file ./${plaintext_file}.back

# open the file for viewing/editing
$editor ./$plaintext_file >&/dev/null

# compare the backup with the one from the editor
if ! diff ./$plaintext_file ./$comp_file >& /dev/null ; then
    # note that diff returns true if the files are identical
    echo "The file $working_dir/$plaintext_file has been modified.  Should I re-encrypt it?"
    select resp in {yes,no} ; do
        if [[ $resp == "yes" ]] ; then
            echo "Backing up $crypt_file"
            /bin/cp -vf ./$crypt_file $backup_dir
            if /usr/bin/gpg --yes --recipient $recipient --encrypt $plaintext_file ; then
                echo "File $plaintext_file has been successfully encrypted to $crypt_file."
            else
                echo "Error encrypting $plaintext_file."
            fi
            break
        elif [[ $resp == "no" ]] ; then
            break
        else
            true # nop
        fi
    done
fi

# delete all plaintext files 
echo "$working_dir/$plaintext_file will be deleted in 3 seconds.  Press ctrl-c to cancel."

for i in {3,2,1} ; do
    echo $i
    sleep 1
done

# (many editors make backup copies)
/bin/rm -f ./$plaintext_file ./$comp_file ./${plaintext_file}.bck ./${plaintext_file}~ ./"#${plaintext_file}#"

```

---

### Post by kfrance on 2007-05-05
I use keepassx.  It keeps my passwords, generates random passwords that can be configured to have numbers or other ascii characters.  It also works on several platforms such as windows.  It is in the fiesty repository by default.

---

### Post by scrooge_74 on 2007-05-05
There is always the old fashion approach: pen and paper

---

### Post by beameup on 2007-05-05
Try Revelation or Keepass. Revelation is in add/Remove

[http://keepass.info/index.html](http://keepass.info/index.html)

---

### Post by Lucifiel on 2007-05-06
Thank you all for the recommendations. I'm downloading Keepass now and will give it a shot. :)

And if it doesn't meet my needs, then I'll move on to Revelation and if not, the GPG method that was suggested in this thread.

Thank you everyone, again, for being patient with my problems and questions. :)

---

