---
title: "Help PowerPC out of the box support"
date: 2012-02-25
forum: Apple Hardware Users
---

### Post by rsavage on 2012-02-25
Hi all,
 
Just a follow up from a thead on the lubuntu qa list. It was commented that ubuntu doesn't detect the battery of laptops. So I've put a bash script together to see if it is possible.
 
Can I get people to test it? I'm after testers with any machine: imacs/emacs/ibooks/powerbooks/powermacs ; you get the idea. 
 
Save the attached file to your home folder and then run it using the command
 
```

./test.sh

```
 
You may have to make it executable first 
 
```

chmod +x test.sh

```
 
[FONT=Verdana]Can you tell me if it detects the battery correctly? Also, I'd be interested to know if you have two batteries do you get the "Battery found" message twice? If you don't have a battery then you should just get a searching message.[/FONT] 
 
[FONT=Verdana]Thanks![/FONT]

---

### Post by rsavage on 2012-02-26
This is what the file contains:

```

#! /bin/sh

# Check for battery

echo "Searching, please wait..."

for dir in $(find "/proc/device-tree/" -type d); do
    name="$(cat "$dir/name" 2>/dev/null || true)"
    device_type="$(cat "$dir/device_type" 2>/dev/null || true)"

        if [ "$name" = battery ]; then
          if [ "$device_type" = battery ]; then
            echo "Battery found"
          fi
        fi
done

```If you prefer, you can just copy the 'for' loop and paste it directly into the terminal.

---

