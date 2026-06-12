---
title: "Just post some code!"
date: 2011-06-18
forum: Cafe Games
---

### Post by PCaddicted on 2011-06-18
OK, here are the rules of this game:
#1.This thread is dedicated to posting code.
#2.You **may** post fake code.
#3.You **may NOT** post malicious code. The forum rules forbid it.
#4.Just post some code!(any code that comes to mind, as long as it's not dangerous).
#5.Have fun!

---

### Post by amauk on 2011-06-18
```
echo "Do I win?"
```

---

### Post by PCaddicted on 2011-06-18
```
sudo post some code
```

---

### Post by cgroza on 2011-06-18
```

while True:
     pass

```

---

### Post by amauk on 2011-06-18
The coolest C code you'll ever come across
```
char*f="char*f=%c%s%c;main(){printf(f,34,f,34);}";main(){printf(f,34,f,34);}
```
Compile and run to see why

---

### Post by Macskeeball on 2011-06-19
I wrote this Java program a few minutes ago just for kicks. It picks a random number between 1 and 100 as a target, and then starting from 0 it adds, subtracts, multiplies, or divides random numbers until it reaches that target value.

```
import java.util.Random;

public class rnTugOfWar {
	public static void main(String[] args) {
		int target, turn, count, progress;
		Random randomNumber = new Random();
		
		count = 0;
		progress = 0;
		target = randomNumber.nextInt(99) + 1; // pick a target between 1 and 100
		
		System.out.println("Target = " + target + "\n"); // display target
		
		while (progress != target){ // keep trying until you get it
			count++;
			turn = randomNumber.nextInt(9) + 1; // for each turn, pick a number between 1 and 10
			
			System.out.print(progress + " "); // print first number in turn's equation
			
			if (progress >= -100 && progress <= 100) { // if between -100 and 100
				if (turn % 2 == 0) { // if turn value is even, add it
					progress += turn;
					System.out.println("+ " + turn + " = " + progress);
				}
				else { // if turn value is odd, subtract it
					progress -= turn;
					System.out.println("- " + turn + " = " + progress);
				}
			}
			else { // If smaller than -100 or larger than 100. This keeps output from getting too far off target.
				if (turn % 2 == 0) { // if turn value is even, multiply by it
					progress *= turn;
					System.out.println("* " + turn + " = " + progress);
				}
				else { // if turn value is odd, divide by it using integer division
					progress /= turn;
					System.out.println("/ " + turn + " = " + progress);
				}
			}
		}
		
		System.out.println("\nTarget reached in " + count + " turns.");
	}
	
}
```

---

### Post by ki4jgt on 2011-06-19
```

while in car:
    pick your nose
    if pick your nose == booger:
        wipe on pants
    else:
        in car

```

---

