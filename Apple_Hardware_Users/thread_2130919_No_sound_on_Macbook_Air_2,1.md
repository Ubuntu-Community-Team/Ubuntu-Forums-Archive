---
title: "No sound on Macbook Air 2,1"
date: 2013-03-30
forum: Apple Hardware Users
---

### Post by Le Gluon du Net on 2013-03-30
Hello,

I installed Ubuntu raring on a Macbook Air 2,1 and I can not get sound work: no soundcard recognized.

The audio card is a Nvidia MCP79 HD

Some logs:

# lspci
00:08.0 Audio device: NVIDIA Corporation MCP79 High Definition Audio (rev b1)


 # lshw -C sound
  *-multimedia NON-RÉCLAMÉ
       description: Audio device
       produit: MCP79 High Definition Audio
       fabriquant: NVIDIA Corporation
       identifiant matériel: 8
       information bus: pci@0000:00:08.0
       version: b1
       bits: 32 bits
       horloge: 66MHz
       fonctionnalités: pm cap_list
       configuration: latency=0 maxlatency=5 mingnt=2
       ressources: mémoire:93380000-93383fff


 # dmesg
[ 1786.009932] hda_intel: Disabling MSI
[ 1786.009970] snd_hda_intel 0000:00:08.0: setting latency timer to 64
[ 1786.042057] hda-intel 0000:00:08.0: no codecs found!


Someone has the same configuration with working sound?

Thank you for your help.

---

