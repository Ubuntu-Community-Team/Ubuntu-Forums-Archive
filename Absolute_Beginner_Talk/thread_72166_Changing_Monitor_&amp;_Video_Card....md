---
title: "Changing Monitor &amp; Video Card..."
date: 2005-10-05
forum: Absolute Beginner Talk
---

### Post by LongTooth on 2005-10-05
Believe it or not, I've used the same monitor since I've been in linux. Now I'm thinking of upgrading it. the same goes for the video card. Despite the fact that I've had several years of experience with Linux I am asking for the proper procedure to implement these changes. 
Rather that just flay away at it, search and surf, I am posting here for two reasons. 1. (Obviously) To make the transition as painless and smoothly as possible -for me!-and 2. So newbies can learn as well. 
So. A change in mointor - From 17" tube to 19" tube. And an addition of a graphics card from an intergraded chip/mother board. I realize I would need to know the HZ and Vz rates. Power, and all the other things that go with a monitor. The same could be said about the new card - brand name, memory, etc. 
That informatin I know I'll need to made this upgrade possible. But it the distro changes that make me hesitate. 
Can some kind soul be good enough to give me (and newbies) the proper way to make this change/upgrade? 
Thanks.

---

### Post by Ampersand on 2005-10-05
After installing your new hardware, you'll just have to run 'sudo dpkg-reconfigure xerver-xorg'. You'll be asked for your keyboard, mouse, video card and monitor details. Generally, the default options will be acceptable. 

You no longer require the frequencies of your monitor. In the more recent versions of Xorg, you can choose between simple, medium and advanced configuration. The simple one just asks for the size of your monitor.

---

