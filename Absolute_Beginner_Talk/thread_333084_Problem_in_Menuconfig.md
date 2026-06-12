---
title: "Problem in Menuconfig"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by tonyr1988 on 2007-01-06
I'm re-building the kernel to work with the MadWifi drivers. These are what I need / don't need:

>     * General setup &#8594; Configure standard kernel features (for small systems) &#8594; Sysctl support: enabled
    * Loadable module support &#8594; Module versioning support: disabled
    * Device Drivers &#8594; Network device support &#8594; Wireless LAN (non-hamradio) &#8594; Wireless LAN drivers (non-hamradio) & Wireless Extensions: enabled
    * Cryptographic options &#8594; Cryptographic API: enabled
    * Cryptographic options &#8594; Cryptographic API &#8594; HMAC support: enabled
    * Cryptographic options &#8594; Cryptographic API &#8594; AES cipher algorithm: enabled (optional, needed for WPA/WPA2 with CCMP) 

I'm to the point where I'm using menuconfig to edit my options. The problem is that some of them (Cryptographic API and HMAC support) show up in the correct spot, but instead of a

[*] or [ ], etc...I see:

--- Cryptographic API
--- HMAC support
<M> Null algorithms
<M> MD4 digest algorithm
etc etc etc...

If I shift-Y them, they stay with the three dashes. Should I be worried, or am I alright? I need both of those enabled - what do the --- mean?

---

