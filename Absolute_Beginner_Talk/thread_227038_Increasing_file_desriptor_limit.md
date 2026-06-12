---
title: "Increasing file desriptor limit"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by Pawka on 2006-08-01
Hallo,

I'm coding multithreaded server with c++, but when it reaches threads limit (arround 380), server unables create any one more. As i guess, increasing file descriptors limit would fix this problem. So, how to increase file descriptor limit?

---

### Post by Pawka on 2006-08-01
Found myself. To change file descriptor limit, u need to use **ulimit** command. You can find its description [here]("http://www.ss64.com/bash/ulimit.html"). To change some limits (for example: The maximum number of open file descriptors), you may need root premissions.

---

