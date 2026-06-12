---
title: "Ahh!! scripting help!"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by elfstone214 on 2007-04-16
Hello all!

I am sure this is a complete noob question but I don't even know where to start looking to learn how to do this.

I need to do the following sequence with a single script:
1) scp some files into a server
2) ssh into the same remote server
3) run a shell script that I have in that server
4) scp somefiles back to my local computer (no clue since I don't know what my address is but my command prompt says "Administrator@merlin")

I know how to do 1-3 manually but how do I put all this into a single script?

Any help or guidance would be great!

---

### Post by bashologist on 2007-04-16
# I havn't used scp in a while, so am not sure if this works.
```
[COLOR="Gray"]# This should work.[/COLOR]
scp -pr /path/to/folder user@###.###.#.###:/path/to/folder/

[COLOR="Gray"]# I'm not sure this will work either![/COLOR]
ssh user@###.###.#.### command

[COLOR="Gray"]# Note the last dot on the following line should copy to your cd.[/COLOR]
scp -pr user@###.###.#.###:/path/to/folder .
```
The remote machine is "user@###.###.#.###" in these examples I think.

---

### Post by elfstone214 on 2007-04-16
bashologist, many thanks for the quick help!

it does work! 

I still have to figure out how to automatically pass in the password with scp but at least I am on my way. Again many thanks!

---

