---
title: "media problem"
date: 2011-06-24
forum: Asus Ubuntu Support (CLOSED)
---

### Post by m_ghv_geo on 2011-06-24
when am playing 720p or 1080p videos does not matter from where hard drive or youtube.com i get frames every 1sec 


THIS NETBOOK CAME WITH WIN 7 AND IT DID NOT HAD ANY PROBLEMS I WAS PLAYING 1080P VIDEOS IN TRIP TO GEORGIA ON PLANE AND DID NOT HAD THIS PROBLEM BUT IN UBUNTU I ONLY CAN WATCH VIDEOS 480P MAX.
 
i have ASUS-1201n-PU17-SL
BASICALLY IT HAS
CPU: INTEL ATOM 1.6GHz DUAL CORE CPU
GPU: NVIDIA ION 
RAM: 2GB

---

### Post by SeijiSensei on 2011-06-25
1) Install the proprietary NVIDIA driver to enable VDPAU decoding of H.264 videos.  Find and run the "Additional Hardware" application.

2) Install a VDPAU-aware application like mplayer.  I usually install smplayer ('sudo apt-get install smplayer') which installs mplayer along with it.  Try that.

3) Don't SHOUT.

---

