---
title: "java command help for linux"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by Ben Sprinkle on 2006-07-18
ok im makin a java game and here my code i got problem with

```

                            case 169: // char screen
				showInterface(3559);
				break;
				case 162: // ancient emote
				stillgfx(435, absY, absX);
				stillgfx(435, absY, absX);
				stillgfx(435, absY, absX);
				stillgfx(435, absY, absX);
				stillgfx(435, absY, absX);
				stillgfx(435, absY, absX);

```

after each still gfx is there a java command to pause like in linux

sleep 2

i need a 2 sec pause in between each one any help?

---

### Post by Ragazzo on 2006-07-18
```

try {
Thread.sleep(2000);
} catch(InterruptedException ex) {
ex.printStackTrace();
}

```

Belongs to Programming Talk.

---

