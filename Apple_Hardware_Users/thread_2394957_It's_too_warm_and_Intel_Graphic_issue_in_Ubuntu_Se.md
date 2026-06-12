---
title: "It's too warm and Intel Graphic issue in Ubuntu Server 18.04 LTS + Macbook Pro 13,3"
date: 2018-06-24
forum: Apple Hardware Users
---

### Post by Daniel Song on 2018-06-24
Hi,

I've installed Ubuntu Server 18.04 LTS on MacBook Pro 13,3.

While using it, it's too warm, and I search the internet, looks like it uses Nvidia driver other than Intel, maybe?

I tried to switch to Intel by prime-select, but it comes with this error:

```

# sudo prime-select intel
Info: selecting the Intel profile
Error: the installed packages do not support PRIME

```

inxi shows like this:

```
inxi -G
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Baffin [Radeon RX 460]
           Display Server: X.org 1.19.6 driver: amdgpu tty size: 195x52 Advanced Data: N/A out of X

```

However, MacBook Pro 13,3 has two graphic chips. One is Intel and the other one is Radeon.

My goal is to make it lower temperature.

Is there any good way to do either make lower temperature or switch to Intel graphics for power saving?

---

