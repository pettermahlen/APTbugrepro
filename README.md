# APTbugrepro

This is a (failed :( ) attempt at reproducing an annotation processing bug we had in our too large application. 
The symptoms when the bug happens are:

1. A package is defined by both a library module and the main app module.
2. Both the library and the main app use auto value annotation processing.
3. The following code gets generated:
  - lib/build/generated/source/debug/<auto-value-implementation-class-from-lib>
  - app/build/generated/source/<variant>/debug/<auto-value-implementation-class-from-lib>
  
That is, the AutoValue_X class from the library gets generated for the application as well, leading to failure when
running Proguard.
