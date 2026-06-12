---
title: "How do I script this?"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by GoUbuntu on 2005-12-16
After playing around with gtkpod, I know what to type in at the terminal to get my contacts from Thunderbird on to my iPod.   How do I put this into a script?

This is what I type in on the terminal:

```
perl mab2vcard ~/.mozilla-thunderbird/h5r6rdt7.default/abook.mab > /media/ipod/Contacts/thunderbird
```

The first argument is the address book, the second argument is the output file.

I think I know that to make a script I create a new file with a .sh extension and put #!/bin/sh in the first line.  I put the commands above in the file, but it doesn't seem to work, the file named "thunderbird" is empty.  

I look forward to your responses.


Thanks,
Brendon

---

### Post by doitashimashite on 2005-12-16
echo "perl mab2vcard ~/.mozilla-thunderbird/h5r6rdt7.default/abook.mab > /media/ipod/Contacts/thunderbird" > thunderbird

chmod +x thunderbird

then start the script by entering

./thunderbird
or
sh thunderbird

You can replace arguments with $1, $2 etc, like in this example:

echo "perl mab2vcard ~/.mozilla-thunderbird/h5r6rdt7.default/$1.mab > /media/ipod/Contacts/$2" > thunderbird

where first argument would be the name of your address book (abook) and second argument the name of your desired output file.

Good luck

---

