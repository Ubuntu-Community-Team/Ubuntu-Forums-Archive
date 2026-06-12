---
title: "possibly broken keyring - apt-get issues"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by psikys on 2007-07-23
Okay, I tried adding a new repository and ran into some problems, somehwere along the lines I start getting this error - 

> sudo apt-get update
Password:
E: The method driver /usr/lib/apt/methods/https could not be found.
E: The method driver /usr/lib/apt/methods/https could not be found.

Someone suggested that perhaps my keyring is broken. Is this true? And if so how do I rebuild the file? I have done a few google searches - only found one hit that actually approached this issue - and the fix didn't work for me.

So if anyone can tell me what it is I am looking at - or how to fix it, it would be GREATLY appreciated.

:mad::mad:

---

### Post by zanglang on 2007-07-24
No, nothing that drastic... You've probably just added a repository that has https:// in front, while apt doesn't support it by default (at least that file doesn't exist for me either :)). Try trimming off the 's' in the repository URL and update apt as usual?

---

