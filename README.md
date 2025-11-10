# 3542-Minimum-Operations-to-Convert-All-Elements-to-Zero

class Solution {
public:
    int minOperations(vector<int>& nums) {
        stack<int> st;
        st.push(0);  // base level
        int ans = 0;

        for (int num : nums) {
            // Pop all higher levels since current num is smaller
            while (!st.empty() && st.top() > num) {
                st.pop();
            }

            // If we encounter a new higher level, count it
            if (st.empty() || st.top() < num) {
                ans++;
                st.push(num);
            }
        }

        return ans;
    }
};
