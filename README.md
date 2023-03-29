# Delivery Driver

[[Udemy] C# Unity 게임 개발자 2D](https://www.udemy.com/course/best-c-unity-2d/) 강의 내용

## 게임 화면

![example.gif](example.gif)

## 게임 설명

드라이버가 물품을 픽업해 배달하는 게임

## 주요 기능

### 1) 카메라 팔로우

```
void LateUpdate()
    {
        transform.position = thingToFollow.transform.position + new Vector3 (0, 0, -10);
    }
```

### 2) 물품 픽업 & 배달

```
private void OnTriggerEnter2D(Collider2D other) {

        if (other.tag == "Package" && !hasPackage)
        {
            Debug.Log("package picked up");
            hasPackage = true;

            spriteRenderer.color = hasPackageColor;

            Destroy(other.gameObject, destroyDelay);

        } else if (other.tag == "Customer" && hasPackage)
        {
            Debug.Log("delivered package");
            hasPackage = false;

            spriteRenderer.color = noPackageColor;
        }

    }
```

### 3) 이동 속도 변화

```
private void OnCollisionEnter2D(Collision2D other) {
        moveSpeed = slowSpeed;
    }

private void OnTriggerEnter2D(Collider2D other) {
        if (other.tag == "Boost") {
            moveSpeed = boostSpeed;
        }
    }
```
