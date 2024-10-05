# Orientation

Orientation is the way that rotation works in Unity. It includes Euler angles and quaternions. Even thought these are the same yet has different uses.
Rotation is the process of changing orientation
Rotation and Orientation is far different from position, both use 3 axes and Vector to represent them but in different use. While position shows where the object is, orientation shows where the object point too.



## Euler angles
Euler /ˈɔɪlə(ɹ)/ angles created by Leonhard Euler. They represent the orientation and rotation of a rigidbody in 3-dimensional using 3 axes X,Y,Z. Unlike vector, they turn X,Y,Z into angle.  Unity way to represent orientation is using the vector property <code>Transform.eulerAngles</code>. <br />
Example:
```C#
using UnityEngine;
public class ExampleScript : MonoBehaviour
{
    void Start()
    {
        transform.eulerAngles = new Vector3(0f,0f,0f);
    }
}
```
**Gimbal locks**
> If you convert to Euler angles to do calculations and rotations, you risk problems with gimbal lock.
>>When an object in 3D space loses a degree of freedom and can only rotate within two dimensions, it’s called gimbal lock. Gimbal lock can occur with Euler angles if two axes become parallel. If you don’t convert the rotational values to Euler angles in your script, the use of quaternions should prevent gimbal lock.<br />
>
Gimbal locks only exist in Gimbals and Euler maths<br/>
In short, Gimbals lock reduces the ability to rotate makes this a big disadvantage.
## Quaternions
Quaternion is similar to euler but represent in 4-axes (X,Y,Z,W). Quaternion does not have *Gimbal locks* and is an advantage. Quaternion instead, does rotation around single axis, which is freely oriented in space.<br/>
Rotation in Unity use quaternion to rotate.<br/>
Example:
```C#
using UnityEngine;
public class ExampleScript : MonoBehaviour
{
    void Start()
    {
        transform.rotation = Quaternion.Euler(0f,0f,0f);
    }
}
```
## Usage
There are 2 ways to represent orientation in computer. Euler angles and Quaternion
## Differences between Euler angles and Quaternion
## Key Differences

| **Feature**              | **Euler Angles**                          | **Quaternions**                        |
|--------------------------|-------------------------------------------|----------------------------------------|
| **Representation**        | 3 angles (X,Y,Z)               | 4 components (x, y, z, w)             |
| **Gimbal Lock**           | Prone to gimbal lock                      | Immune to gimbal lock                 |
| **Ease of Understanding** | Human-readable                 | Difficult to visualize                |
| **Interpolation**         | Complex and less efficient                | Smooth and efficient (slerp)          |
| **Order Sensitivity**     | Rotation order matters                    | Rotation order is irrelevant          |
| **Usage**                 | UI, simple animations, aerospace          | Robotics, VR/AR, gaming, graphics     |
| **Computational Cost**    | Lower for simple scenarios                | More efficient for complex rotations  |

## Relations between Euler angles and Quaternions
Even through 2 things are different, in the end they still represent rotation and orientation. You can convert both of them with function in Unity.<br/>
To convert from Euler angles to quaternions, you can use the <code>Quaternion.Euler</code> function.<br/>
To convert a quaternion to Euler angles, you can use the <code>Quaternion.eulerAngles</code> function.
## Source
[Video](https://www.youtube.com/watch?v=sJcVJEOwLUs)<br/>
[Unity 1](https://docs.unity3d.com/Manual/QuaternionAndEulerRotationsInUnity.html)<br/>
[Unity 2](https://docs.unity3d.com/ScriptReference/Transform-eulerAngles.html)<br/>
