---
title: "classpoint variable does not exsist"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by Jacques Kleynhans on 2008-03-02
i changed a section of my bash to include this 
tos2x() {
        export TOSROOT=/opt/tinyos-2.x
	export TOSDIR=$TOSROOT/tos
	export CLASSPATH=$TOSROOT/support/sdk/java/tinyos.jar:.
	export MAKERULES=$TOSROOT/support/make/Makerules
	export PATH=$PATH:/opt/msp430/bin	
}

Your classpath should contain  and a pointer 
to the cwd (a dot)

i there anything wrong here??

---

