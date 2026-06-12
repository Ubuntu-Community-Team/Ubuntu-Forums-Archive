---
title: "Frets on Fire dosn't work!"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by yamfox on 2008-03-10
I can't get the game Frets on Fire to work. Here is the commad line output
```

yamfox@yamfox:~$ fretsonfire
Traceback (most recent call last):
  File "./FretsOnFire.py", line 64, in <module>
    engine = GameEngine(config)
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 155, in __init__
    self.video.setMode((width, height), fullscreen = fullscreen, multisamples = multisamples)
  File "/usr/share/games/fretsonfire/game/Video.py", line 68, in setMode
    self.screen = pygame.display.set_mode(resolution, flags)
pygame.error: Couldn't find matching GLX visual

```

---

### Post by jacob01 on 2008-03-10
is this the fof from the ubuntu repository or the official linux client from the source forge site??


( i have had better luck with the one from the repository, it runs faster)

---

