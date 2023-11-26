# 분할 정복 알고리즘 (Divide and Conquer)
주어진 문제의 입력을 분할하여(divide) 문제를 해결(정복, conquer)하는 방식의 알고리즘

## 합병 정렬 (Merge Sort)
- 입력이 2개인 부분 문제로 분할
- 부분 문제의 크기가 ½로 감소하는 divide and conquer 알고리즘
- 합병 과정이 문제를 정복하는 과정

- 시간 복잡도 : O(nlogn)
    - (층수) X O(n) = log2n X O(n) = O(nlogn)
    - 분할 과정 : O(1) / 합병 과정: O(m+n)
    - 합병은 입력 크기에 비례하므로 각 층에서의 비교 횟수는 O(n)
    - 층의 최대 개수 : 2^k = n >  k = log2n

- 공간 복잡도 : O(n)
    - 입력을 위한 메모리 공간과 O(1) 크기의 메모리 공간만 사용

- 예제코드
```
MergeSort(A,p,q)
입력: A[p]~A[q]
출력: 정렬된 A[p]~A[q]

1. if (p < q) { // 배열의 원소의 수가 2개 이상이면
2. k = floor((p+q)/2) // k는 중간 원소의 인덱스
3. MergeSort(A,p,k) // 앞부분 순환 호출
4. MergeSort(A,k+1,q) // 뒷부분 순환 호출
5. A[p]~A[k]와 A[k+1]~A[q]를 합병
}

# floor(a) : a보다 작은 가장 큰 정수
```

## 퀵 정렬 (Quick Sort)
- 문제를 2개의 부분 문제로 분할
- 각 부분 문제의 크기가 일정하지 않은 형태의 divide and conquer 알고리즘
  
- Pivot 선정 방법
    - 랜덤
    - 가장 왼쪽 숫자, 중간 숫자, 가장 오른쪽 숫자 중에서 중앙값으로 pivot 결정
    - Median-of-Medians : 3 등분 후, 각 부분에서 가장 왼쪽 숫자, 중간 숫자, 가장 오른쪽 숫자 중에 중앙값을 찾은 후, 세 중앙값들 중에서 중앙값을 pivot으로 선정
          
- 특징
    - 큰 입력(n)에 대해 가장 좋은 성능(pivot)을 보임

- 시간 복잡도 : 최악의 경우: O(n^2) / 최선의 경우: O(nlogn)
    - pivot 선택에 의해 결정
    - 최악의 경우 :  (n-1)+(n-2)+(n-3)+ + 2+1 = n(n-1)/2 = O(n^2)
    - 최선의 경우
        - 각 층에서 비교 횟수 : O(n)
        - O(n) X (층수) = O(n) X logn = O(nlogn)

- 공간 복잡도 : O(n)
    - 입력을 위한 메모리 공간과 O(1) 크기의 메모리 공간만 사용

- 예제코드
```
QuickSort(A, left, right)
입력: 배열 A[left]~A[right]
출력: 정렬된 배열 A[left]~A[right]

1. if (left < right) {
2. 피봇을 A[left]~A[right]에서 선택하고, 피봇을 A[left]와 자리를 바꾼 후, 피봇과 배열의 각 원소를 비교하여 피봇보다 작은 숫자들은 A[left]~A[p-1]으로 옮기고, 피봇보다 큰 숫자들은 A[p+1]~A[right]으로 옮기며, 피봇은 A[p]에 놓는다.
3. QuickSort(A, left, p-1) // 피봇보다 작은 그룹
4. QuickSort(A, p+1, right) // 피봇보다 큰 그룹
}
```