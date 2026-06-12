---
title: "Java/Eclipse"
date: 2005-01-23
forum: Apple PPC Users
---

### Post by frodoweb on 2005-01-23
en_EN: Hello list,
es_ES: Hola lista,

en_EN: I have a Ibook G4 (the last - 23.01.05) where are installed
Debian Ubuntu 4.01 to PPC (logical)
es_ES: Dispongo de un Ibook G4 (el ultimo - 23.01.05) donde corre una
Debian ubuntu 4.01 para ppc (logicamente).

en_EN: I want to install Java and Eclipse to development. The SDK of
Java is "easy" because can be downloaded to [www.ibm.com](www.ibm.com) the version
"1.4.2 SR1"
es_ES: Desearia instalar Java y Eclipse para desarrollo. El SDK de
java esta "sencillo" debido a que se puede descargar facilmente de
[www.ibm.com](www.ibm.com) la version "1.4.2 SR1"

en_EN: But... How i can install eclipse IDE?¿
es_ES: Pero... el eclipse como puedo conseguirlo?¿.

en_EN: I search in Google and have find two solutions:
es_ES: Desde luego no pregunto sin antes ir a San Google, y este me ha
mostrado dos opciones:

en_EN: 1. Compiling since source code:
es_ES: 1. Compilarlo desde las fuentes descrito en:
[http://download.eclipse.org/downloads/drops/R-3.0.1-200409161125/srcIncludedBuildInstructions.html](http://download.eclipse.org/downloads/drops/R-3.0.1-200409161125/srcIncludedBuildInstructions.html)

en_EN: Compiling only specific parts of eclipse x86
es_ES: 2. Compilar partes expecificas desde la version oficial del
eclipse x86 descrito en:
[http://www.rexi.org/linux/eclipse-ppc.html](http://www.rexi.org/linux/eclipse-ppc.html)

en_EN: In the first option, this is the output error:
es_ES: En la primera opcion obtengo este error al hacer el "build -os ...."

JVMDG217: Dump Handler is Processing Signal 4 - Please Wait.
JVMDG303: JVM Requesting Java core file
JVMDG304: Java core file written to
/home/frodo/eclipse_src/javacore.20050123.123151.6641.txt
JVMDG215: Dump Handler has Processed Exception Signal 4.
./build: line 60:  6641 Instrucción ilegal      ant -buildfile
build.xml $target -DinstallOs=$os -DinstallWs=$ws -DinstallArch=$arch
-Dbootclasspath=$bootclasspath -DjavacTarget=1.2

en_EN: In the second option where recompiling SWT don´t create the 3
.so (only libswt-gtk-3036-so) and although continue with the process
and eclipse executable was created, where i start eclipse only can see
bootsplash before that the output error was:
es_ES: En la segunda opcion al recompilar SWT no se crean los 3 .so
(solo libswt-gtk-3036.so) y aunque siga con el proceso y se cree el
ejecutable eclipse, al iniciarlo solo se muestra el bootsplash antes
de dar el error:

JVMDG217: Dump Handler is Processing Signal 4 - Please Wait.
JVMDG303: JVM Requesting Java core file
JVMDG304: Java core file written to
/home/frodo/eclipse/javacore.20050123.123452.6704.txt
JVMDG215: Dump Handler has Processed Exception Signal 4.

en_EN: I think that the error is in SDK of ibm.com :(. Can i find the solution?¿
es_ES: No tengo muchas esperanzas en que alguien encuentre solucion,
porque creo que el error esta en el SDK de ibm.com.

en_EN: Bye and thanks
es_ES: Agradeceria todo tipo de ayuda. SALUDOS ;)

---

### Post by Viro on 2005-01-23
In the terminal before running any Java apps, you need to type the commands export JITC_PROCESSOR_TYPE=6

It's a bug in the IBM JDK that doesn't seem to be corrected even in the latest version of the JDK.

---

### Post by frodoweb on 2005-01-23
I have this in .bashrc.

well, i think that not exist solution yet  :cry:

---

