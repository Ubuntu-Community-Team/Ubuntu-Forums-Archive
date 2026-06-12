---
title: "acpi wake up script fix"
date: 2021-04-14
forum: Apple Hardware Users
---

### Post by ahbart on 2021-04-14
I've Ubuntu 20.10 running on a laptop.
It is running very well, but I still have a small issue with power management. When I close the lid, the laptop suspends. But when I open it, it does not wake up. 
I want to echo LID0 and XHC1 to /proc/acpi/wakeup when one or both of them are disabled.

I've found a script, that was working wel for others. This is the original script:
```
#!/bin/bash

declare -a devices=("EHC1 EHC2 XHCI") # <-- Add your entries here
for device in "${devices[@]}"; do
    if grep -qw ^$device.*enabled /proc/acpi/wakeup; then
        sudo sh -c "echo $device > /proc/acpi/wakeup"
    fi
done
```

In: "cat /proc/acpi/wakeup" these are the XHC1 and LID0 items:
```
XHC1      S3    *disabled   pci:0000:00:14.0 
LID0      S4    *disabled  platform:PNP0C0D:00
```

I changed the script like this:
```
#!/bin/bash
declare -a devices=("XHC1 LID0")
for device in "${devices[@]}"; do
    if grep -qw ^$device.*disabled /proc/acpi/wakeup; then
        sudo sh -c "echo $device > /proc/acpi/wakeup"
    fi
done
```
But than I get this error:
```
grep: LID0.*disabled: File or folder does not exist
```
When I change the code like this: 
```
declare -a devices=("XHC1")
```
so by removing 1 device, then the code works. 

Can someone help me solve this script problem?

---

### Post by ahbart on 2021-04-15
No one with a little bash script knowledge who can help me?

---

### Post by howefield on 2021-04-15
Thread moved to the "Apple Hardware Users" forum.

---

### Post by ahbart on 2021-04-15
This is not apple related, nor apple hardware related. This is power management, acpi, laptop related. So I do not understand why this is moved to the apple hardware forum?! I shoud not have mentioned that This is on an Macbook. 
I'm lokking for an bash script solution related to acpi. Can someone place it back please to Hardware?

---

### Post by CelticWarrior on 2021-04-15
> **ahbart said:**
> This is not apple related, nor apple hardware related. This is powermanagement, acpi, laptop related. So I do not understand why this is moved to the apple hardware forum?!

Quoting from the OP:
> [COLOR=#000000]It runs on a macbook pro mid 2012[/COLOR]

Apple hardware often has specific characteristics. They're anything but "generic" laptops, so it makes sense to be moved to this section. Either way it'll probably remain as it is.

---

### Post by ahbart on 2021-04-15
" Apple hardware often has specific characteristics" . I agree to that. But this is related to the way how LID0 and XHC1 can be set to enabled via a bash script. See above. 
So I do not agree.

---

### Post by CelticWarrior on 2021-04-15
Not agreeing is your prerogative, of course. Will it change the mods minds? Probably not. Being in any other section improves the chances to have a reply? Very likely not.

---

### Post by ahbart on 2021-04-15
I have a bash script problem. Nothing to do with this specific Apple hardware. 
The exposure in this threat is much smaller then in Hardware. I'm totally not happy with this!

---

### Post by QIII on 2021-04-15
The exposure in this sub-forum is exactly the same as in any other.  It is no less visible here than in any other thread.  It is not hidden or obscured.

But it might more likely catch the eye of someone with similar hardware.

---

### Post by ahbart on 2021-04-16
I totally disagree with you moderators in this! My post was and is about bash scripting. The fact that Ubuntu is running on a macbook is totally irrelevant here. Maybe I should not have mentioned that in the first place. 
In my opinion it is just rude or even arrogant to not even listen to my arguments to leave it under the hardware topics. 
On another forum I've got an answer to my bash scripting question. I have to leave out the quotes from the declare line like this:
```
declare -a devices=( EHC1 EHC2 XHCI )
```

---

