---
title: "dpkg error"
date: 2006-01-18
forum: Absolute Beginner Talk
---

### Post by DevyD on 2006-01-18
Hi

I recently installed a packege by using the "sudo dpkg -i" command, but when I try to install another package by using that command it gives me the error, "database are is locked by another process".

Can anyone please tell me how to stop that process or what this error means?



Thanks

---

### Post by 23meg on 2006-01-18
That error means that apt is somehow working; it's likely that you're either in the process of installing/uninstalling something else via apt in another terminal window, or Synaptic is running. Quit all other instances of apt and try again.

---

### Post by DevyD on 2006-01-18
Thanks for your quick response, but can you please tell me how to quit the instances of app?

Thanks

---

### Post by Mustard on 2006-01-18
[QUOTE=DevyD]Thanks for your quick response, but can you please tell me how to quit the instances of app?

Thanks[/QUOTE]

Ideally you would have synaptic closed and no other terminals windows going that are currently executing apt-get or dpkg related commands.

---

### Post by DevyD on 2006-01-18
[QUOTE=Mustard]Ideally you would have synaptic closed and no other terminals windows going that are currently executing apt-get or dpkg related commands.[/QUOTE]


Thanks.

---

