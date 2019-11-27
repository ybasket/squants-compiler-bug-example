### Minimal example for https://github.com/scala/bug/issues/11734
Fails to compile with Scala 2.13, succeeds with 2.12.10. Replacing the wildcard import in one of the files in the motion package
solves the problem on 2.13 as well, problematic seems only the cycle between
`class Velocity extends TimeIntegral[Acceleration]`
and
`class Acceleration extends TimeDerivative[Velocity]`
when both reference each other via a type alias defined in the `squants` package object.
