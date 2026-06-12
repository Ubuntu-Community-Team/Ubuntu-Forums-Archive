---
title: "Trying to Nvidia GeForce 320M card work in a MacBook Air Late 2010"
date: 2020-06-24
forum: Apple Hardware Users
---

### Post by notoman2 on 2020-06-24
Hi, i am trying to follow these steps ([https://askubuntu.com/questions/264247/proprietary-nvidia-drivers-with-efi-on-mac-to-prevent-overheating/613573#613573](https://askubuntu.com/questions/264247/proprietary-nvidia-drivers-with-efi-on-mac-to-prevent-overheating/613573#613573)) to accomplish the NVidia drivers to work in a Late 2010 Mac Book Air.
I did it before on a Linux Mint MATE distribution, but I wanted a lightweight version and a more stable system.
So it is a little tricky now. I ended in this situation ([https://askubuntu.com/questions/878548/setpci-doesnt-change-the-register-value-for-the-bridge-device-nvidia-driver-bl](https://askubuntu.com/questions/878548/setpci-doesnt-change-the-register-value-for-the-bridge-device-nvidia-driver-bl))
Now I'm stuck in this part: 
> Create x86_64-efi folder.
Ubuntu folder in /boot/EFI/ can be different on your machine depends how you named it in OS installation process, do not paste it. Replace it with correct path.
```
sudo mkdir /boot/EFI/ubuntu/x86_64-efi

```
Copy setpci module files into grub2 folder
```
sudo cp /usr/lib/grub/x86_64-efi/setpci.* /boot/EFI/ubuntu/x86_64-efi

```

Which path should I point making the dir?
I am very newbie, and I appreciate a lot any of your help!
Thank you!

---

